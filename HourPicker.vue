<template>
  <v-app>
    <div>
      <form>
        <div class="mb-4">
          <label for="servicio" class="form-label"
            ><b>Seleccione la fecha y hora de la Actividad</b></label
          >
          <v-date-picker
            v-model="date"
            mode="dateTime"
            :min-date="new Date()"
            :valid-hours="[8, 10, 12, 16, 20]"
            :minute-increment="60"
            is24hr
          >
            <template #default="{ inputValue, inputEvents }">
              <div class="flex sm:flex-row justify-start items-center">
                <!-- <div class="flex flex-col sm:flex-row justify-start items-center"> -->
                <div class="relative flex-grow">
                  <svg
                    class="text-gray-600 w-4 h-full mx-2 absolute pointer-events-none"
                    fill="none"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
                    />
                  </svg>
                  <input
                    class="flex-grow pl-8 pr-2 py-1 bg-gray-100 border rounded w-full"
                    :value="inputValue"
                    v-on="inputEvents"
                  />
                </div>
              </div>
            </template>
          </v-date-picker>
        </div>
      </form>
    </div>
  </v-app>
</template>

<script>
export default {
  name: "HourPicker",
  emits: ["obtain-date-range"],
  data() {
    return {
      date: new Date(),
      masks: {
        input: "DD-MM-YYYY HH:mm",
      },
    };
  },
  watch: {
    date(newRange) {
      this.$emit("obtain-date-range", newRange);
    },
  },
};
</script>
