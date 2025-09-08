# API Документация

<link href="https://cdn.jsdelivr.net/npm/redoc@next/bundles/redoc.standalone.js" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/redoc@next/bundles/redoc.standalone.js"> </script>

<div id="redoc-container"></div>

<script>
  window.onload = function() {
    fetch('/api/openapi.yaml')
      .then(response => response.text())
      .then(yaml => {
        const spec = window.jsyaml.load(yaml);
        Redoc.init(spec, {
          theme: {
            spacing: {
              sectionVertical: '60px'
            }
          },
          scrollYOffset: 70,
          hideDownloadButton: false,
          expandResponses: "all"
        }, document.getElementById('redoc-container'));
      })
      .catch(err => {
        document.getElementById('redoc-container').innerHTML = 
          `<p style="color: red;">Ошибка: ${err.message}</p>`;
      });
  };
</script>

<style>
  #redoc-container {
    margin-top: 20px;
  }
</style>
