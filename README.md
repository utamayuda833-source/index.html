<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>Yuda · App Developer</title>
  <!-- Font Awesome Icons (gratis) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Roboto, system-ui, -apple-system, sans-serif;
      background: linear-gradient(145deg, #0c0f14 0%, #141a21 100%);
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 1.5rem;
      margin: 0;
      color: #eef2f7;
    }

    /* Kartu profil utama – glassmorphism modern */
    .profile-card {
      background: rgba(24, 30, 38, 0.75);
      backdrop-filter: blur(14px) saturate(180%);
      -webkit-backdrop-filter: blur(14px) saturate(180%);
      border-radius: 56px 56px 48px 48px;
      box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.8), 0 0 0 1px rgba(255, 255, 255, 0.04);
      max-width: 500px;
      width: 100%;
      padding: 2.2rem 2rem 2.5rem;
      transition: all 0.2s ease;
      border: 1px solid rgba(255, 255, 255, 0.02);
    }

    /* avatar / ikon kepala */
    .avatar-wrapper {
      display: flex;
      justify-content: center;
      margin-bottom: 1.2rem;
    }

    .avatar-icon {
      background: linear-gradient(135deg, #2b3b4f, #1b2533);
      width: 110px;
      height: 110px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3.8rem;
      color: #b6cdff;
      box-shadow: 0 12px 28px rgba(0, 0, 0, 0.7), inset 0 1px 0 rgba(255, 255, 255, 0.08);
      border: 1px solid rgba(255, 255, 255, 0.06);
      transition: 0.2s;
    }

    .avatar-icon i {
      filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.5));
    }

    /* Nama & profesi */
    .name-title {
      text-align: center;
      margin-bottom: 1.8rem;
    }

    .name-title h1 {
      font-size: 2.2rem;
      font-weight: 700;
      letter-spacing: -0.5px;
      background: linear-gradient(to right, #f0f6ff, #c8dcff);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      margin-bottom: 0.25rem;
      line-height: 1.2;
      word-break: break-word;
    }

    .name-title .badge-profesi {
      display: inline-block;
      background: rgba(70, 130, 200, 0.18);
      backdrop-filter: blur(4px);
      padding: 0.35rem 1.4rem;
      border-radius: 60px;
      font-weight: 500;
      font-size: 1rem;
      color: #b4d0ff;
      letter-spacing: 0.3px;
      border: 1px solid rgba(100, 160, 255, 0.15);
      box-shadow: 0 2px 8px rgba(0, 20, 40, 0.3);
      margin-top: 4px;
    }

    .badge-profesi i {
      margin-right: 6px;
      font-size: 0.9rem;
      color: #7aa9ff;
    }

    /* garis pemisah halus */
    .divider {
      width: 70px;
      height: 2px;
      background: linear-gradient(90deg, transparent, #3f6a9f, transparent);
      margin: 0.4rem auto 1.8rem auto;
      border-radius: 10px;
      opacity: 0.5;
    }

    /* daftar kontak — seperti list item dengan ikon */
    .contact-list {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      margin: 1.8rem 0 2.2rem;
    }

    .contact-item {
      display: flex;
      align-items: center;
      background: rgba(0, 0, 0, 0.25);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
      padding: 0.8rem 1.2rem;
      border-radius: 60px;
      border: 1px solid rgba(255, 255, 255, 0.03);
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
      transition: all 0.2s ease;
      text-decoration: none;
      color: #eef2f7;
      cursor: default;
    }

    .contact-item:hover {
      background: rgba(40, 60, 90, 0.35);
      border-color: rgba(120, 180, 255, 0.15);
      transform: scale(1.01);
      box-shadow: 0 8px 18px rgba(0, 0, 0, 0.5);
    }

    .contact-item .icon-circle {
      width: 42px;
      height: 42px;
      border-radius: 50%;
      background: rgba(30, 45, 70, 0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 1rem;
      flex-shrink: 0;
      font-size: 1.2rem;
      color: #aac3ff;
      border: 1px solid rgba(255, 255, 255, 0.05);
    }

    .contact-item .contact-info {
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .contact-item .contact-label {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      opacity: 0.5;
      font-weight: 500;
      line-height: 1.2;
    }

    .contact-item .contact-value {
      font-weight: 500;
      font-size: 1rem;
      word-break: break-word;
      color: #f0f6ff;
      letter-spacing: -0.2px;
    }

    .contact-item .contact-value i {
      margin-right: 4px;
      color: #7aa9ff;
      font-size: 0.85rem;
    }

    /* tautan WA / email dibuat klikable dengan efek */
    .contact-item.clickable {
      cursor: pointer;
    }

    .contact-item.clickable:hover .contact-value {
      color: #b4d9ff;
    }

    .contact-item.clickable:active {
      transform: scale(0.98);
    }

    /* sosial media — grid dua tombol */
    .social-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
      margin-top: 0.8rem;
    }

    .social-btn {
      background: rgba(0, 0, 0, 0.25);
      backdrop-filter: blur(4px);
      -webkit-backdrop-filter: blur(4px);
      border: 1px solid rgba(255, 255, 255, 0.03);
      padding: 0.9rem 0.5rem;
      border-radius: 60px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      font-size: 1rem;
      font-weight: 500;
      color: #d6e5ff;
      text-decoration: none;
      transition: 0.2s ease;
      box-shadow: 0 6px 12px rgba(0, 0, 0, 0.25);
      cursor: pointer;
    }

    .social-btn i {
      font-size: 1.4rem;
      color: #b0ccff;
      transition: 0.2s;
    }

    .social-btn:hover {
      background: rgba(50, 80, 130, 0.3);
      border-color: rgba(110, 170, 255, 0.2);
      transform: translateY(-2px);
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.5);
    }

    .social-btn:active {
      transform: scale(0.96);
    }

    .social-btn .btn-label {
      font-size: 0.9rem;
      letter-spacing: 0.3px;
    }

    /* footer kecil */
    .footer-note {
      margin-top: 2.2rem;
      text-align: center;
      font-size: 0.7rem;
      opacity: 0.25;
      letter-spacing: 0.5px;
      border-top: 1px solid rgba(255, 255, 255, 0.02);
      padding-top: 1.5rem;
    }

    /* responsif untuk layar kecil */
    @media (max-width: 440px) {
      .profile-card {
        padding: 1.8rem 1.2rem 2rem;
        border-radius: 40px;
      }
      .name-title h1 {
        font-size: 1.9rem;
      }
      .avatar-icon {
        width: 90px;
        height: 90px;
        font-size: 3.2rem;
      }
      .contact-item {
        padding: 0.6rem 1rem;
      }
      .contact-item .icon-circle {
        width: 36px;
        height: 36px;
        font-size: 1rem;
        margin-right: 0.8rem;
      }
      .social-grid {
        gap: 0.7rem;
      }
      .social-btn {
        padding: 0.7rem 0.3rem;
        font-size: 0.9rem;
      }
    }

    /* smooth */
    a, .contact-item, .social-btn {
      -webkit-tap-highlight-color: transparent;
    }
  </style>
</head>
<body>

  <div class="profile-card">

    <!-- Avatar ikon -->
    <div class="avatar-wrapper">
      <div class="avatar-icon">
        <i class="fas fa-user-astronaut"></i>
      </div>
    </div>

    <!-- Nama & profesi -->
    <div class="name-title">
      <h1>AHMAD YUDA PRAHASTA</h1>
      <div class="badge-profesi">
        <i class="fas fa-code"></i> App Developer
      </div>
      <div class="divider"></div>
    </div>

    <!-- Daftar kontak (email, WA) -->
    <div class="contact-list">

      <!-- Email -->
      <a href="mailto:yudaprahasta890@gmail.com" class="contact-item clickable" title="Kirim email">
        <div class="icon-circle"><i class="fas fa-envelope"></i></div>
        <div class="contact-info">
          <span class="contact-label">Email</span>
          <span class="contact-value"><i class="fas fa-at"></i> yudaprahasta890@gmail.com</span>
        </div>
      </a>

      <!-- WhatsApp -->
      <a href="https://wa.me/6289514870891?text=Halo%20Yuda%2C%20saya%20lihat%20profil%20Anda." target="_blank" class="contact-item clickable" title="Chat WhatsApp">
        <div class="icon-circle"><i class="fab fa-whatsapp"></i></div>
        <div class="contact-info">
          <span class="contact-label">WhatsApp</span>
          <span class="contact-value"><i class="fas fa-phone-alt"></i> 0895-1487-0891</span>
        </div>
      </a>
    </div>

    <!-- Sosial media: Instagram & TikTok -->
    <div class="social-grid">
      <a href="https://instagram.com/YUDAPRAHASTA58" target="_blank" class="social-btn" title="Buka Instagram">
        <i class="fab fa-instagram"></i>
        <span class="btn-label">@YUDAPRAHASTA58</span>
      </a>
      <a href="https://tiktok.com/@YUDAPRAHASTA68" target="_blank" class="social-btn" title="Buka TikTok">
        <i class="fab fa-tiktok"></i>
        <span class="btn-label">@YUDAPRAHASTA68</span>
      </a>
    </div>

    <!-- footer kecil (opsional) -->
    <div class="footer-note">
      <i class="fas fa-asterisk" style="opacity: 0.3; margin-right: 4px;"></i>  app developer · yuda
    </div>
  </div>

</body>
</html>
