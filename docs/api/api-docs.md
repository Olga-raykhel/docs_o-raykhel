# API Документация

<script src="https://unpkg.com/swagger-ui-dist@4/swagger-ui-bundle.js"></script>
<link rel="stylesheet" href="https://unpkg.com/swagger-ui-dist@4/swagger-ui.css" />

<div id="swagger-ui"></div>

<script>
  window.onload = function() {
    fetch('/api/openapi.json')  // ← путь к твоему JSON-файлу
      .then(response => {
        if (!response.ok) throw new Error('Файл не найден');
        return response.json();
      })
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
        console.error("Ошибка:", err);
        document.getElementById('swagger-ui').innerHTML = 
          `<p style="color: red;">Не удалось загрузить API-документацию. Проверьте путь к <code>openapi.json</code>.</p>`;
      });
  };
</script>
