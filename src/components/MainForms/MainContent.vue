<template>
  <main class="main-content">
    <div class="file-upload-container">
      <img
        src="../../assets/left-arrow.png"
        alt="Left Arrow"
        class="arrow-icon"
      />
      <input type="file" @change="uploadFile" class="upload-button" />
      <img
        src="../../assets/right-arrow.png"
        alt="Right Arrow"
        class="arrow-icon"
      />
    </div>

    <div class="storage-options">
      <label
        class="storage-option"
        v-for="option in storageOptions"
        :key="option.days"
      >
        <input
          type="radio"
          name="storage-duration"
          :value="option.days"
          v-model="selectedDuration"
          class="storage-option-input"
        />
        <span
          class="storage-option-text"
          @mouseover="showTooltip(option)"
          @mouseleave="hideTooltip"
          >{{ option.label }}</span
        >
        <span class="tooltip" v-if="option.show">{{ option.tooltip }}</span>
      </label>
    </div>
    <button v-if="fileLink" @click="getFileLink" class="get-file-button">
      Получить ссылку
    </button>
  </main>
</template>

<script>
export default {
  name: "MainContent",
  data() {
    return {
      selectedDuration: "1",
      uploadedFile: null,
      fileLink: "",
      storageOptions: [
        {
          label: "1 раз",
          days: "1",
          tooltip: "Файлы будут удалены после 1го скачивания",
          show: false,
        },
        {
          label: "3 дня",
          days: "3",
          tooltip: "Срок хранения файлов - 3 дня",
          show: false,
        },
        {
          label: "14 дней",
          days: "14",
          tooltip: "Срок хранения файлов 14 дней",
          show: false,
        },
      ],
    };
  },
  methods: {
    uploadFile() {
      alert("Еще не реализованно");
      const file = event.target.files[0];
      if (file) {
        const formData = new FormData();
        formData.append("file", file);
        this.uploadedFile = file;
        this.fileLink = `./Files/${file.name}`;
      }
      console.log("Файл выбран, срок хранения:", this.selectedDuration);
    },
    showTooltip(option) {
      option.show = true;
    },
    hideTooltip(option) {
      option.show = false;
    },
    getFileLink() {
      alert(`Ссылка на файл: ${this.fileLink}`);
    },
  },
};
</script>

<style scoped>
.main-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  margin: auto;
  width: 100%;
  padding: 2rem;
}

.file-upload-container {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 2rem;
}

.arrow-icon {
  width: 50px;
  height: auto;
}

.upload-button {
  display: flex;
  justify-content: center;
  align-items: center;
  align-self: center;
  padding: 1rem 2rem;
  font-size: 1rem;
  cursor: pointer;
}

.storage-options {
  display: flex;
  justify-content: center;
}

.storage-option {
  margin: 0 1rem;
  position: relative;
}

.storage-option-text {
  cursor: pointer;
  color: #fff;
}

input[type="radio"]:checked + span {
  font-weight: bold;
}

.tooltip {
  position: absolute;
  display: none;
  background-color: #555;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 5px 10px;
  z-index: 1;
  bottom: 150%;
  left: 50%;
  margin-left: -60px;
  opacity: 0;
  transition: opacity 0.3s;
}

.tooltip::after {
  content: "";
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #555 transparent transparent transparent;
}

.storage-option-text:hover + .tooltip {
  display: block;
  visibility: visible;
  opacity: 1;
}

.get-file-button {
  padding: 0.5rem 1rem;
  margin-top: 1rem;
  color: #fff;
  background-color: #b19f9e;
  border-radius: 0.25rem;
  cursor: pointer;
  border: none;
  outline: none;
}

.get-file-button:hover {
  background-color: #c2a1a0;
}
</style>
