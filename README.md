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
      <a href="{{ url_for('index') }}">🏠 Home</a>
      <a href="{{ url_for('post') }}">✏️ Post</a>
    </nav>
  </header>
  <main>
    {% block content %}{% endblock %}
  </main>
  <footer>
    <p>&copy; 2025 chun2web - ちゅん2web</p>
  </footer>
</body>
</html>
{% extends 'layout.html' %}
{% block content %}
  <section class="posts">
    {% for p in posts %}
      <article class="post">
        <h2>{{ p.title }}</h2>
        <time datetime="{{ p.created_at }}">{{ p.created_at }}</time>
        <p>{{ p.body|replace('\n', '<br>')|safe }}</p>
      </article>
    {% else %}
      <p>まだ投稿がありません。</p>
    {% endfor %}
  </section>
{% endblock %}
{% extends 'layout.html' %}
{% block content %}
  <section class="post-form">
    {% if error %}
      <p class="error">{{ error }}</p>
    {% endif %}
    <form action="{{ url_for('post') }}" method="post">
      <label>🔑 投稿パスワード：
        <input type="password" name="password" required>
      </label>
      <label>📌 タイトル：
        <input type="text" name="title" required>
      </label>
      <label>📝 本文：
        <textarea name="body" rows="6" required></textarea>
      </label>
      <button type="submit">🍀 投稿する</button>
    </form>
  </section>
{% endblock %}
{% extends 'layout.html' %}
{% block content %}
  <section class="thanks">
    <h2>🌸 投稿ありがとうございました！</h2>
    <p>ちゅん2webにようこそ。また書いてね。</p>
    <a class="button" href="{{ url_for('index') }}">🏠 トップページへ戻る</a>
    <a class="button" href="{{ url_for('post') }}">✏️ もう一度投稿する</a>
  </section>
{% endblock %}