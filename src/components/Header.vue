<template>
  <header class="app-header">
    <div class="logo">
      <img
        src="../assets/logo.png"
        alt="FileShare Logo"
        class="app-header__logo"
      />
      <span>FileSharing</span>
    </div>
    <div class="container">
      <nav class="app-header__nav">
        <ul>
          <li
            v-for="item in menuItems"
            :key="item.id"
            @click="ShowFunction(item.text)"
          >
            <a :class="item.className">{{ item.text }}</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {
      menuItems: [
        { id: 1, text: "Главная", className: "menu-elem" },
        { id: 4, text: "ЧаВо", className: "menu-elem" },
        { id: 5, text: "Обратная связь", className: "menu-elem" },
        {
          id: 6,
          text: "Пожертвовать",
          className: "btn btn-donate",
        },
      ],
    };
  },
  methods: {
    ShowFunction(itemText) {
      const sections = {
        Главная: "Main",
        ЧаВо: "FaQ",
        "Обратная связь": "FeedBack",
        Пожертвовать: "Donate",
      };

      // ID-шники
      const allSections = Object.values(sections);

      // Прячем
      allSections.forEach((sectionId) => {
        document.getElementById(sectionId).style.display = "none";
      });
      const sectionToShow = sections[itemText];
      if (sectionToShow && document.getElementById(sectionToShow)) {
        document.getElementById(sectionToShow).style.display = "block";
      }
    },
  },
};
</script>

<style scoped>
.app-header {
  background-color: #b19f9e;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 1rem 0;
}

.app-header.container {
  max-width: 1170px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  flex-direction: column;
}

.app-header__logo {
  height: 50px;
}

.app-header__nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  gap: 20px;
}

.app-header__nav ul li a {
  text-decoration: none;
  color: #333;
  transition: color 0.3s;
}

.app-header__nav ul li a:hover {
  color: #75663c;
}

.btn-donate {
  background-color: #ffdd57;
  padding: 0.5rem 1rem;
  color: #333;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.btn-donate:hover {
  background-color: #ffc107;
}

li {
  cursor: pointer;
}

.menu-elem {
  cursor: pointer;
  color: #333;
  background-color: #a16e83;
  padding: 0.5rem 1rem;
  text-decoration: none;
  border-radius: 5px;
  transition: background-color 0.3s;
}

btn:hover {
  cursor: pointer;
}
</style>
