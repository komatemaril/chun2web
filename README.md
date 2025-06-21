# chun2web
ちゅん2web
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>chun2web</title>
  <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>
  <header>
    <h1>🍀 chun2web</h1>
    <nav>
      <a href="{{ url_for('index') }}">Home</a>
      <a href="{{ url_for('post') }}">Post</a>
    </nav>
  </header>
  <main>
    {% block content %}{% endblock %}
  </main>
  <footer>
    <p>&copy; 2025 chun2web</p>
  </footer>
</body>
</html>