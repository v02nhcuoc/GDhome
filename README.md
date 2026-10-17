<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
  <title>Đang mở bản vẽ 3D...</title>
</head>
<body style="background:#10141d;color:#fff;font-family:sans-serif;display:flex;align-items:center;justify-content:center;height:100vh;margin:0;">
  <div id="msg">⏳ Đang tải bản vẽ 3D...</div>
  <script>
    const gistId = location.search.replace('?', '').replace('id=', '').trim();
    if (!gistId) {
      document.getElementById('msg').innerText = 'Thiếu mã bản vẽ!';
    } else {
      fetch('https://api.github.com/gists/' + gistId)
        .then(r => r.json())
        .then(data => {
          const file = Object.values(data.files)[0];
          document.open();
          document.write(file.content);
          document.close();
        })
        .catch(e => { document.getElementById('msg').innerText = 'Lỗi tải bản vẽ: ' + e.message; });
    }
  </script>
</body>
</html>
