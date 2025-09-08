# API Документация (Swagger UI)

<script src="https://unpkg.com/swagger-ui-dist@4/swagger-ui-bundle.js"></script>
<link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@4/swagger-ui.css" />

<div id="swagger-ui"></div>

<script>
  window.onload = function() {
    fetch('/api/swagger.json')  // ← слэш в начале!
      .then(response => response.json())
      .then(spec => {
        window.ui = SwaggerUIBundle({
          spec: spec,
          dom_id: '#swagger-ui',
          presets: [
            SwaggerUIBundle.presets.apis,
            SwaggerUIBundle.presets.syntaxHighlighting
          ],
          layout: "BaseLayout"
        });
      })
      .catch(err => {
        console.error("Ошибка:", err);
        document.getElementById('swagger-ui').innerHTML = 
          '<p style="color: red;">Не удалось загрузить swagger.json. Проверьте путь.</p>';
      });
  };
</script>
