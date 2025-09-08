# API Документация (Swagger UI)

<script src="https://unpkg.com/swagger-ui-dist@4/swagger-ui-bundle.js"></script>
<link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@4/swagger-ui.css" />

<div id="swagger-ui"></div>

<script>
  window.onload = function() {
    // Загружаем  swagger.yml (путь относительно site/)
    fetch('api/swagger.yaml')
      .then(response => response.yaml())
      .then(spec => {
        window.ui = SwaggerUIBundle({
          spec: spec,
          dom_id: '#swagger-ui',
          presets: [
            SwaggerUIBundle.presets.apis,
            SwaggerUIBundle.presets.syntaxHighlighting
          ],
          layout: "BaseLayout",
          deepLinking: true,
          showExtensions: true,
          showCommonExtensions: true
        });
      })
      .catch(err => {
        console.error("Ошибка загрузки swagger.yaml:", err);
        document.getElementById('swagger-ui').innerHTML = '<p style="color: red;">Не удалось загрузить спецификацию API. Проверьте, доступен ли файл <code>swagger.json</code>.</p>';
      });
  };
</script>
