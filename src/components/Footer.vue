<template>
  <div class="help">
    <footer class="footer">
      <div class="footer-content">
        <span>© 2023 FileSharing, Inc. Все права защищены</span>
        <div class="footer-links">
          <a href="https://vk.com" target="_blank" class="footer-link">ВК</a>
          <a href="https://telegram.org" target="_blank" class="footer-link"
            >Телеграм</a
          >
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "AppFooter",
};
</script>

<style scoped>
.footer {
  padding: 20px;
  background-color: #b19f9e;
  text-align: center;
  border-top: 1px solid #eaeaea;
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.footer-links {
  display: flex;
  gap: 10px;
  margin-top: 10px;
}

.footer-link {
  text-decoration: none;
  color: #007bff;
  transition: color 0.3s ease;

  /* simple hover effect */
  &:hover {
    color: #0056b3;
  }
}
</style>
