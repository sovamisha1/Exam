<template>
  <div class="faq-container">
    <h1 class="faq-title">Часто Задаваемые Вопросы</h1>
    <div class="faq" v-for="(faq, index) in faqs" :key="index">
      <h3 class="faq-question" @click="toggleFAQ(index)">
        {{ faq.question }}
      </h3>
      <p class="faq-answer" v-if="faq.visible">
        {{ faq.answer }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FAQPage",
  data() {
    return {
      faqs: [
        {
          question: "Как работает наш файлообменник?",
          answer:
            "Наш файлообменник позволяет пользователям безопасно загружать и скачивать файлы. После загрузки файла пользователь получает уникальную ссылку, которую можно поделиться с другими. Когда файл скачивают, он автоматически удаляется с сервера в соответствии с выбранными настройками.",
          visible: false,
        },
        {
          question: "Как файл удаляется после одного скачивания?",
          answer:
            "Когда вы загружаете файл, вы можете выбрать опцию 'Удалить после первого скачивания'. Как только файл будет скачан один раз, система автоматически удалит его с сервера.",
          visible: false,
        },
        {
          question: "Что произойдет с файлом после трех дней?",
          answer:
            "Если выбрана опция 'Удалить после трех дней', файл будет храниться на наших серверах в течение трех дней после его загрузки. По истечении этого срока файл будет автоматически удален вне зависимости от того, сколько раз он был скачан.",
          visible: false,
        },
        {
          question: "Можно ли сохранить файл дольше, например 14 дней?",
          answer:
            "Да, вы можете выбрать опцию 'Удалить после четырнадцати дней', и ваш файл будет доступен для скачивания в течение 14 дней. После этого срока файл будет удален с сервера.",
          visible: false,
        },
      ],
    };
  },
  methods: {
    toggleFAQ(index) {
      this.faqs[index].visible = !this.faqs[index].visible;
    },
  },
};
</script>

<style>
.faq-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.faq-title {
  text-align: center;
  margin-bottom: 40px;
  color: #fff;
}

.faq-question {
  cursor: pointer;
  background-color: #f5f5f5;
  padding: 15px 20px;
  margin: 10px 0;
  border-radius: 5px;
  width: 760px;
  transition: background-color 0.3s ease;
}

.faq-question:hover {
  background-color: #eaeaea;
}

.faq-answer {
  padding: 0 20px 20px;
  border-left: 3px solid #00b4d8;
  color: #fff;
  margin: 0 0 10px;
}
</style>
