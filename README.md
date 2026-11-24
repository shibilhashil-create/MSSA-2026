<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Old Students Meet — Dec 6, 2026 | Ma'dinul Uloom Da'wa & Dars</title>

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700;800;900&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">

  <!-- QR Generator, Ticket PNG Export, and Live QR Scanner -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
  <script src="https://unpkg.com/html5-qrcode@2.3.8/html5-qrcode.min.js"></script>

  <style>
    :root {
      --bg-dark: #02120c;
      --emerald: #10b981;
      --emerald-bright: #34d399;
      --gold: #f59e0b;
      --gold-soft: #fde68a;
      --glass-bg: rgba(4, 24, 17, 0.78);
      --glass-border: rgba(52, 211, 153, 0.25);
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
      --danger: #f87171;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background-color: var(--bg-dark);
      color: var(--text-main);
      min-height: 100vh;
      line-height: 1.55;
      overflow-x: hidden;
    }

    /* Full-Screen Background Image */
    .bg-stage {
      position: fixed;
      inset: 0;
      z-index: -2;
      background-image: url('background.jpg');
      background-size: cover;
      background-position: center top;
      background-repeat: no-repeat;
      transform: scale(1.02);
    }

    .bg-overlay {
      position: fixed;
      inset: 0;
      z-index: -1;
      background:
        radial-gradient(circle at 50% 18%, rgba(16, 185, 129, 0.24) 0%, rgba(2, 18, 12, 0.78) 55%, rgba(2, 12, 8, 0.95) 100%),
        linear-gradient(180deg, rgba(2, 16, 11, 0.62) 0%, rgba(2, 18, 12, 0.86) 55%, rgba(2, 12, 8, 0.96) 100%);
    }

    /* Navbar */
    .navbar {
      position: sticky;
      top: 0;
      z-index: 50;
      background: rgba(2, 18, 12, 0.78);
      backdrop-filter: blur(14px);
      -webkit-backdrop-filter: blur(14px);
      border-bottom: 1px solid rgba(52, 211, 153, 0.16);
      padding: 0.8rem 1.25rem;
    }

    .nav-inner {
      max-width: 1040px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 0.75rem;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 0.65rem;
      text-decoration: none;
      color: #fff;
    }

    .brand-icon {
      width: 38px;
      height: 38px;
      border-radius: 10px;
      background: linear-gradient(135deg, #10b981, #059669);
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 18px rgba(16, 185, 129, 0.4);
      flex-shrink: 0;
    }

    .brand-text strong {
      display: block;
      font-family: 'Outfit', sans-serif;
      font-size: 0.92rem;
      font-weight: 700;
      line-height: 1.15;
    }

    .brand-text span {
      font-size: 0.7rem;
      color: var(--emerald-bright);
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 0.55rem;
    }

    .nav-admin-btn {
      background: rgba(255, 255, 255, 0.08);
      border: 1px solid rgba(255, 255, 255, 0.18);
      color: #e2e8f0;
      font-family: 'Outfit', sans-serif;
      font-size: 0.8rem;
      font-weight: 600;
      padding: 0.48rem 0.9rem;
      border-radius: 999px;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      transition: all 0.2s;
    }

    .nav-admin-btn:hover {
      background: rgba(245, 158, 11, 0.2);
      border-color: var(--gold);
      color: var(--gold-soft);
    }

    .nav-cta {
      background: linear-gradient(135deg, #10b981 0%, #059669 100%);
      color: #02120c;
      text-decoration: none;
      font-family: 'Outfit', sans-serif;
      font-size: 0.82rem;
      font-weight: 800;
      padding: 0.5rem 1.05rem;
      border-radius: 999px;
      white-space: nowrap;
      box-shadow: 0 0 18px rgba(16, 185, 129, 0.35);
    }

    /* Hero */
    .hero {
      max-width: 960px;
      margin: 0 auto;
      padding: 3rem 1.25rem 2rem;
      text-align: center;
    }

    .summit-pill {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: rgba(16, 185, 129, 0.15);
      border: 1px solid rgba(52, 211, 153, 0.42);
      color: #a7f3d0;
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 0.38rem 1rem;
      border-radius: 999px;
      margin-bottom: 1.15rem;
    }

    .pulse-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: #34d399;
      box-shadow: 0 0 10px #34d399;
      animation: pulse 1.8s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.4; transform: scale(1.3); }
    }

    .hero-institution {
      font-family: 'Outfit', sans-serif;
      font-size: clamp(0.95rem, 2.2vw, 1.18rem);
      font-weight: 700;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      color: var(--gold-soft);
      margin-bottom: 0.4rem;
    }

    .hero h1 {
      font-family: 'Outfit', sans-serif;
      font-size: clamp(2.3rem, 6.5vw, 4.1rem);
      font-weight: 900;
      line-height: 1.05;
      letter-spacing: -0.025em;
      margin-bottom: 0.85rem;
      background: linear-gradient(180deg, #ffffff 15%, #a7f3d0 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .hero p {
      color: #cbd5e1;
      font-size: clamp(0.92rem, 2vw, 1.05rem);
      max-width: 580px;
      margin: 0 auto 1.5rem;
    }

    /* Countdown Bar */
    .countdown {
      display: inline-flex;
      gap: 0.65rem;
      margin-bottom: 1.75rem;
      flex-wrap: wrap;
      justify-content: center;
    }

    .cd-box {
      min-width: 68px;
      background: rgba(4, 28, 20, 0.75);
      border: 1px solid rgba(52, 211, 153, 0.28);
      border-radius: 12px;
      padding: 0.55rem 0.7rem;
      backdrop-filter: blur(8px);
    }

    .cd-box strong {
      display: block;
      font-family: 'Outfit', sans-serif;
      font-size: 1.45rem;
      font-weight: 800;
      color: var(--gold-soft);
      line-height: 1.1;
    }

    .cd-box span {
      font-size: 0.65rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: #94a3b8;
      font-weight: 700;
    }

    /* Info Cards */
    .info-strip {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 0.85rem;
      max-width: 860px;
      margin: 0 auto;
    }

    .info-card {
      background: rgba(4, 28, 20, 0.7);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(52, 211, 153, 0.22);
      border-radius: 14px;
      padding: 0.95rem 1.05rem;
      text-align: left;
      display: flex;
      align-items: flex-start;
      gap: 0.75rem;
    }

    .info-icon {
      width: 36px;
      height: 36px;
      border-radius: 10px;
      background: rgba(16, 185, 129, 0.16);
      color: var(--emerald-bright);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    .info-card small {
      display: block;
      font-size: 0.66rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: #94a3b8;
      font-weight: 700;
      margin-bottom: 0.15rem;
    }

    .info-card strong {
      font-size: 0.88rem;
      font-weight: 700;
      color: #fff;
      line-height: 1.3;
      display: block;
    }

    /* Main Container */
    .main-wrap {
      max-width: 840px;
      margin: 1rem auto 4rem;
      padding: 0 1.1rem;
    }

    .glass-panel {
      background: var(--glass-bg);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid var(--glass-border);
      border-radius: 24px;
      padding: 2.1rem;
      box-shadow: 0 28px 60px -15px rgba(0, 0, 0, 0.65);
      animation: fadeUp 0.4s ease;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(16px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .panel-header {
      margin-bottom: 1.65rem;
      border-bottom: 1px solid rgba(255, 255, 255, 0.08);
      padding-bottom: 1rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 0.75rem;
    }

    .panel-header h2 {
      font-family: 'Outfit', sans-serif;
      font-size: 1.5rem;
      font-weight: 800;
      color: #fff;
      margin-bottom: 0.2rem;
    }

    .panel-header p { font-size: 0.88rem; color: #94a3b8; }

    /* Photo Dropzone */
    .photo-dropzone {
      display: flex;
      align-items: center;
      gap: 1.2rem;
      padding: 1.15rem;
      border-radius: 16px;
      background: rgba(2, 18, 12, 0.55);
      border: 1.5px dashed rgba(52, 211, 153, 0.42);
      margin-bottom: 1.45rem;
    }

    .avatar-circle {
      width: 84px;
      height: 84px;
      border-radius: 50%;
      background: rgba(16, 185, 129, 0.14);
      border: 2.5px solid rgba(52, 211, 153, 0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      flex-shrink: 0;
      color: var(--emerald-bright);
    }

    .avatar-circle img { width: 100%; height: 100%; object-fit: cover; display: none; }
    .upload-meta h4 { font-size: 0.95rem; font-weight: 700; margin-bottom: 0.15rem; }
    .upload-meta p { font-size: 0.78rem; color: #94a3b8; margin-bottom: 0.65rem; }

    .btn-choose-photo {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      background: rgba(16, 185, 129, 0.18);
      border: 1px solid rgba(52, 211, 153, 0.5);
      color: #a7f3d0;
      font-size: 0.82rem;
      font-weight: 600;
      padding: 0.46rem 0.95rem;
      border-radius: 10px;
      cursor: pointer;
    }

    .btn-choose-photo:hover { background: var(--emerald); color: #02120c; }

    /* Form Controls */
    .form-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.1rem; }
    .form-group label { display: block; font-size: 0.82rem; font-weight: 600; color: #cbd5e1; margin-bottom: 0.4rem; }
    .req { color: #fbbf24; }

    .form-control {
      width: 100%;
      padding: 0.78rem 1rem;
      border-radius: 12px;
      border: 1.5px solid rgba(148, 163, 184, 0.25);
      background: rgba(2, 16, 11, 0.68);
      color: #fff;
      font-family: inherit;
      font-size: 0.94rem;
    }

    .form-control::placeholder { color: #64748b; }
    .form-control:focus {
      outline: none;
      border-color: var(--emerald-bright);
      box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.22);
    }

    input[type="date"]::-webkit-calendar-picker-indicator { filter: invert(1) opacity(0.75); cursor: pointer; }
    .error-msg { color: var(--danger); font-size: 0.76rem; margin-top: 0.3rem; display: none; }

    .btn-submit {
      width: 100%;
      margin-top: 1.65rem;
      padding: 0.98rem 1.5rem;
      border: none;
      border-radius: 14px;
      background: linear-gradient(135deg, #10b981 0%, #059669 100%);
      color: #02120c;
      font-family: 'Outfit', sans-serif;
      font-size: 1.06rem;
      font-weight: 800;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 0.55rem;
      box-shadow: 0 14px 30px -10px rgba(16, 185, 129, 0.55);
      transition: all 0.2s;
    }

    .btn-submit:disabled { opacity: 0.7; cursor: wait; }
    .btn-submit:hover:not(:disabled) { transform: translateY(-2px); filter: brightness(1.06); }

    /* ============================================================
       DIGITAL TICKET
    ============================================================ */
    #ticketSection { display: none; }

    .confirmed-pill {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.6rem;
      background: rgba(16, 185, 129, 0.16);
      border: 1px solid rgba(52, 211, 153, 0.4);
      color: #a7f3d0;
      padding: 0.85rem 1.15rem;
      border-radius: 14px;
      font-size: 0.88rem;
      font-weight: 600;
      margin-bottom: 1.5rem;
      text-align: center;
    }

    .ticket-stage { display: flex; justify-content: center; margin-bottom: 1.6rem; }

    #digitalTicket {
      width: 100%;
      max-width: 420px;
      background: linear-gradient(160deg, #04281b 0%, #021710 55%, #010e09 100%);
      border-radius: 22px;
      overflow: hidden;
      border: 1.5px solid #10b981;
      box-shadow: 0 24px 50px rgba(0, 0, 0, 0.65);
      color: #fff;
    }

    .ticket-top-accent { height: 6px; background: linear-gradient(90deg, #059669 0%, #34d399 45%, #fbbf24 100%); }

    .ticket-header {
      padding: 1.3rem 1.4rem 1.05rem;
      background: linear-gradient(135deg, #064e3b 0%, #03261b 100%);
      border-bottom: 1px solid rgba(52, 211, 153, 0.25);
    }

    .ticket-header-row { display: flex; justify-content: space-between; align-items: center; gap: 0.5rem; margin-bottom: 0.5rem; }
    .ticket-inst { font-family: 'Outfit', sans-serif; font-size: 0.72rem; font-weight: 800; letter-spacing: 0.09em; text-transform: uppercase; color: #fde68a; }
    .ticket-verified { background: rgba(16, 185, 129, 0.22); border: 1px solid #34d399; color: #a7f3d0; font-size: 0.64rem; font-weight: 800; padding: 0.18rem 0.55rem; border-radius: 999px; white-space: nowrap; }
    .ticket-title { font-family: 'Outfit', sans-serif; font-size: 1.42rem; font-weight: 900; line-height: 1.15; margin-bottom: 0.2rem; }
    .ticket-sub { font-size: 0.78rem; color: #a7f3d0; font-weight: 600; }

    .ticket-body { padding: 1.3rem 1.4rem 1.05rem; }
    .ticket-profile { display: flex; align-items: center; gap: 1rem; padding-bottom: 1.05rem; margin-bottom: 1.05rem; border-bottom: 1px solid rgba(255, 255, 255, 0.1); }
    .ticket-avatar { width: 82px; height: 82px; border-radius: 16px; border: 2.5px solid #34d399; object-fit: cover; flex-shrink: 0; background: #064e3b; }
    .ticket-name { font-family: 'Outfit', sans-serif; font-size: 1.25rem; font-weight: 800; line-height: 1.2; margin-bottom: 0.35rem; word-break: break-word; }
    .ticket-batch-pill { display: inline-block; background: rgba(251, 191, 36, 0.18); border: 1px solid rgba(251, 191, 36, 0.45); color: #fde68a; font-size: 0.74rem; font-weight: 700; padding: 0.18rem 0.65rem; border-radius: 6px; }

    .ticket-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.85rem 0.75rem; }
    .t-field label { display: block; font-size: 0.64rem; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; color: #6ee7b7; margin-bottom: 0.12rem; }
    .t-field span { display: block; font-size: 0.84rem; font-weight: 600; color: #f1f5f9; word-break: break-word; }
    .t-field-full { grid-column: 1 / -1; background: rgba(16, 185, 129, 0.1); border: 1px solid rgba(52, 211, 153, 0.22); border-radius: 10px; padding: 0.62rem 0.8rem; margin-top: 0.15rem; }

    .ticket-tear { position: relative; height: 24px; display: flex; align-items: center; }
    .ticket-tear::before { content: ""; width: 100%; border-top: 2px dashed rgba(52, 211, 153, 0.35); }
    .cutout { position: absolute; width: 22px; height: 22px; border-radius: 50%; background: #041811; border: 1.5px solid #10b981; top: 50%; transform: translateY(-50%); }
    .cutout-l { left: -12px; }
    .cutout-r { right: -12px; }

    .ticket-qr-footer { padding: 0.85rem 1.4rem 1.35rem; display: flex; align-items: center; justify-content: space-between; gap: 1rem; background: #02120c; }
    .qr-info { flex: 1; }
    .pass-id-lbl { font-size: 0.64rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.1em; color: #94a3b8; }
    .pass-id-val { font-family: 'Outfit', monospace; font-size: 1.12rem; font-weight: 800; color: #fde68a; letter-spacing: 0.05em; margin-bottom: 0.35rem; }
    .qr-note { font-size: 0.72rem; color: #94a3b8; line-height: 1.35; }
    .qr-white-box { background: #fff; padding: 8px; border-radius: 12px; flex-shrink: 0; display: flex; align-items: center; justify-content: center; }
    .qr-white-box img, .qr-white-box canvas { display: block; width: 98px !important; height: 98px !important; }

    .actions-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.75rem; max-width: 420px; margin: 0 auto; }
    .btn-act { display: inline-flex; align-items: center; justify-content: center; gap: 0.45rem; padding: 0.84rem 1rem; border-radius: 12px; font-family: inherit; font-size: 0.88rem; font-weight: 700; border: none; cursor: pointer; transition: all 0.2s; }
    .btn-dl { grid-column: 1 / -1; background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%); color: #02120c; font-size: 0.96rem; }
    .btn-native-share { background: rgba(16, 185, 129, 0.2); border: 1px solid rgba(52, 211, 153, 0.5); color: #a7f3d0; }
    .btn-wa { background: #16a34a; color: #fff; }
    .btn-again { grid-column: 1 / -1; background: rgba(255, 255, 255, 0.07); border: 1px solid rgba(255, 255, 255, 0.16); color: #e2e8f0; }

    /* ============================================================
       ADMIN-ONLY PANEL (QR SCANNER + CODE VERIFY + DASHBOARD)
    ============================================================ */
    #adminPanelSection { display: none; }

    .admin-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      background: rgba(245, 158, 11, 0.18);
      border: 1px solid rgba(245, 158, 11, 0.5);
      color: var(--gold-soft);
      font-size: 0.72rem;
      font-weight: 800;
      padding: 0.28rem 0.7rem;
      border-radius: 999px;
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    .btn-logout {
      background: rgba(248, 113, 113, 0.16);
      border: 1px solid rgba(248, 113, 113, 0.4);
      color: #fca5a5;
      padding: 0.45rem 0.9rem;
      border-radius: 10px;
      font-size: 0.8rem;
      font-weight: 700;
      cursor: pointer;
    }

    .sync-pill {
      font-size: 0.75rem;
      padding: 0.35rem 0.75rem;
      border-radius: 8px;
      margin-bottom: 1.25rem;
      display: inline-flex;
      align-items: center;
      gap: 0.45rem;
      font-weight: 600;
    }
    .sync-cloud { background: rgba(16, 185, 129, 0.16); color: #6ee7b7; border: 1px solid rgba(52, 211, 153, 0.35); }
    .sync-local { background: rgba(245, 158, 11, 0.15); color: #fde68a; border: 1px solid rgba(245, 158, 11, 0.35); }

    /* Admin Stats */
    .stats-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 0.8rem;
      margin-bottom: 1.5rem;
    }

    .stat-card {
      background: rgba(2, 16, 11, 0.65);
      border: 1px solid rgba(52, 211, 153, 0.2);
      border-radius: 14px;
      padding: 1rem;
      text-align: center;
    }

    .stat-card strong {
      display: block;
      font-family: 'Outfit', sans-serif;
      font-size: 1.85rem;
      font-weight: 800;
      color: #fff;
      line-height: 1.1;
    }

    .stat-card.stat-green strong { color: #34d399; }
    .stat-card.stat-gold strong { color: #fde68a; }
    .stat-card span { font-size: 0.72rem; text-transform: uppercase; letter-spacing: 0.08em; color: #94a3b8; font-weight: 700; }

    /* Admin Tabs */
    .admin-tabs {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 0.5rem;
      background: rgba(2, 16, 11, 0.7);
      padding: 0.4rem;
      border-radius: 14px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      margin-bottom: 1.5rem;
    }

    .tab-btn {
      background: transparent;
      border: none;
      color: #94a3b8;
      font-family: 'Outfit', sans-serif;
      font-size: 0.86rem;
      font-weight: 700;
      padding: 0.65rem 0.5rem;
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .tab-btn.active {
      background: linear-gradient(135deg, #10b981, #059669);
      color: #02120c;
    }

    .tab-pane { display: none; }
    .tab-pane.active { display: block; animation: fadeUp 0.25s ease; }

    /* QR Scanner Box */
    .scanner-box {
      background: rgba(2, 16, 11, 0.75);
      border: 1.5px solid rgba(52, 211, 153, 0.3);
      border-radius: 16px;
      padding: 1.25rem;
      text-align: center;
    }

    #qrReader {
      width: 100%;
      max-width: 420px;
      margin: 0 auto 1rem;
      border-radius: 14px;
      overflow: hidden;
      background: #000;
    }

    .scanner-controls { display: flex; justify-content: center; gap: 0.75rem; flex-wrap: wrap; }

    .btn-cam {
      padding: 0.7rem 1.25rem;
      border-radius: 10px;
      font-weight: 700;
      font-size: 0.88rem;
      border: none;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 0.45rem;
    }

    .btn-cam-start { background: #10b981; color: #02120c; }
    .btn-cam-stop { background: rgba(248, 113, 113, 0.2); border: 1px solid #f87171; color: #fca5a5; display: none; }

    /* Manual Code Entry */
    .manual-box {
      background: rgba(2, 16, 11, 0.75);
      border: 1.5px solid rgba(52, 211, 153, 0.3);
      border-radius: 16px;
      padding: 1.35rem;
    }

    .manual-row { display: flex; gap: 0.65rem; margin-top: 0.65rem; }
    .manual-row input { flex: 1; text-transform: uppercase; letter-spacing: 0.05em; font-weight: 700; }
    .btn-verify {
      background: linear-gradient(135deg, #f59e0b, #d97706);
      color: #02120c;
      border: none;
      border-radius: 12px;
      padding: 0 1.4rem;
      font-family: 'Outfit', sans-serif;
      font-weight: 800;
      font-size: 0.92rem;
      cursor: pointer;
      white-space: nowrap;
    }

    /* Verification Result Card */
    #verifyResultCard {
      display: none;
      margin-top: 1.35rem;
      border-radius: 16px;
      padding: 1.35rem;
      animation: fadeUp 0.25s ease;
    }

    .res-valid { background: rgba(16, 185, 129, 0.14); border: 1.5px solid #10b981; }
    .res-warn { background: rgba(245, 158, 11, 0.15); border: 1.5px solid #f59e0b; }
    .res-invalid { background: rgba(248, 113, 113, 0.15); border: 1.5px solid #f87171; }

    .res-status-title { font-family: 'Outfit', sans-serif; font-size: 1.15rem; font-weight: 800; margin-bottom: 0.75rem; display: flex; align-items: center; gap: 0.5rem; }
    .res-attendee-row { display: flex; align-items: center; gap: 1rem; margin-bottom: 1rem; }
    .res-thumb { width: 64px; height: 64px; border-radius: 12px; object-fit: cover; border: 2px solid #34d399; background: #064e3b; flex-shrink: 0; }
    .res-meta-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 0.65rem; font-size: 0.84rem; margin-bottom: 1rem; }
    .res-meta-grid small { display: block; font-size: 0.68rem; color: #94a3b8; text-transform: uppercase; font-weight: 700; }

    .btn-checkin-now {
      width: 100%;
      padding: 0.9rem;
      border-radius: 12px;
      border: none;
      background: linear-gradient(135deg, #10b981, #059669);
      color: #02120c;
      font-family: 'Outfit', sans-serif;
      font-size: 1rem;
      font-weight: 800;
      cursor: pointer;
    }

    /* Attendee Table */
    .table-tools { display: flex; gap: 0.65rem; margin-bottom: 1rem; flex-wrap: wrap; }
    .table-tools input { flex: 1; min-width: 180px; }
    .btn-tool {
      background: rgba(16, 185, 129, 0.16);
      border: 1px solid rgba(52, 211, 153, 0.45);
      color: #a7f3d0;
      padding: 0.65rem 1rem;
      border-radius: 10px;
      font-size: 0.82rem;
      font-weight: 700;
      cursor: pointer;
    }

    .table-wrap { overflow-x: auto; border-radius: 12px; border: 1px solid rgba(255, 255, 255, 0.1); }
    table { width: 100%; border-collapse: collapse; font-size: 0.82rem; text-align: left; }
    th, td { padding: 0.75rem 0.8rem; border-bottom: 1px solid rgba(255, 255, 255, 0.07); }
    th { background: rgba(2, 16, 11, 0.85); color: #6ee7b7; font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.07em; }
    .status-chip { padding: 0.2rem 0.55rem; border-radius: 999px; font-size: 0.7rem; font-weight: 700; white-space: nowrap; }
    .chip-in { background: rgba(16, 185, 129, 0.2); color: #6ee7b7; }
    .chip-reg { background: rgba(245, 158, 11, 0.18); color: #fde68a; }

    /* Admin Login Modal */
    .modal-backdrop {
      position: fixed;
      inset: 0;
      background: rgba(2, 12, 8, 0.84);
      backdrop-filter: blur(8px);
      z-index: 200;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 1rem;
    }

    .modal-backdrop.open { display: flex; }

    .modal-card {
      width: 100%;
      max-width: 390px;
      background: #041d14;
      border: 1.5px solid rgba(52, 211, 153, 0.35);
      border-radius: 20px;
      padding: 1.8rem;
      box-shadow: 0 25px 50px rgba(0, 0, 0, 0.7);
      text-align: center;
    }

    .modal-card h3 { font-family: 'Outfit', sans-serif; font-size: 1.35rem; margin-bottom: 0.35rem; }
    .modal-card p { font-size: 0.84rem; color: #94a3b8; margin-bottom: 1.25rem; }
    .modal-btns { display: grid; grid-template-columns: 1fr 1fr; gap: 0.65rem; margin-top: 1rem; }

    /* Footer & Floating BG Picker */
    footer { text-align: center; padding: 1.5rem 1rem 3rem; color: #94a3b8; font-size: 0.82rem; }

    .bg-picker-btn {
      position: fixed;
      bottom: 16px;
      right: 16px;
      z-index: 60;
      background: rgba(2, 18, 12, 0.85);
      border: 1px solid rgba(52, 211, 153, 0.35);
      color: #a7f3d0;
      font-size: 0.72rem;
      font-weight: 600;
      padding: 0.42rem 0.75rem;
      border-radius: 999px;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 0.35rem;
      opacity: 0.75;
    }
    .bg-picker-btn:hover { opacity: 1; }

    .toast {
      position: fixed;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%) translateY(80px);
      background: #10b981;
      color: #02120c;
      padding: 0.75rem 1.35rem;
      border-radius: 999px;
      font-size: 0.86rem;
      font-weight: 700;
      box-shadow: 0 14px 28px rgba(0, 0, 0, 0.45);
      opacity: 0;
      transition: all 0.3s ease;
      z-index: 999;
      white-space: nowrap;
    }
    .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

    @media (max-width: 768px) {
      .info-strip { grid-template-columns: 1fr; }
    }
    @media (max-width: 600px) {
      .hero { padding-top: 2.2rem; }
      .glass-panel { padding: 1.35rem; border-radius: 18px; }
      .form-grid, .stats-row { grid-template-columns: 1fr; }
      .photo-dropzone { flex-direction: column; text-align: center; }
      .ticket-qr-footer { flex-direction: column-reverse; text-align: center; }
      .manual-row { flex-direction: column; }
      .btn-verify { padding: 0.82rem; }
      .nav-cta { display: none; }
    }
  </style>
</head>
<body>

  <!-- Background Stage Photo -->
  <div class="bg-stage" id="bgStage"></div>
  <div class="bg-overlay"></div>

  <!-- Navbar -->
  <nav class="navbar">
    <div class="nav-inner">
      <a href="#" class="brand" id="navHomeBtn">
        <div class="brand-icon">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#02120c" stroke-width="2.4"><path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/></svg>
        </div>
        <div class="brand-text">
          <strong>Ma'dinul Uloom Da'wa & Dars</strong>
          <span>Kochannur • Dec 6, 2026</span>
        </div>
      </a>
      <div class="nav-actions">
        <button type="button" class="nav-admin-btn" id="openAdminLoginBtn">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>
          Admin Panel
        </button>
        <a href="#register" class="nav-cta">Register Now</a>
      </div>
    </div>
  </nav>

  <!-- Hero Section -->
  <header class="hero" id="heroSection">
    <div class="summit-pill">
      <span class="pulse-dot"></span>
      <span>Old Students Programme • December 6, 2026</span>
    </div>
    <div class="hero-institution">MA'DINUL ULOOM DA'WA & DARS</div>
    <h1>OLD STUDENTS MEET</h1>
    <p>Join our blessed alumni gathering at Kochannur Main Hall. Register now to receive your official QR Digital Entry Pass.</p>

    <!-- Live Countdown to Dec 6, 2026 -->
    <div class="countdown" id="countdownBox">
      <div class="cd-box"><strong id="cdDays">00</strong><span>Days</span></div>
      <div class="cd-box"><strong id="cdHours">00</strong><span>Hours</span></div>
      <div class="cd-box"><strong id="cdMins">00</strong><span>Mins</span></div>
      <div class="cd-box"><strong id="cdSecs">00</strong><span>Secs</span></div>
    </div>

    <div class="info-strip">
      <div class="info-card">
        <div class="info-icon">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>
        </div>
        <div>
          <small>Event Date</small>
          <strong>December 6, 2026 (Sunday)</strong>
        </div>
      </div>

      <div class="info-card">
        <div class="info-icon">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>
        </div>
        <div>
          <small>Venue Location</small>
          <strong>Ma'dinul Uloom Dars, Kochannur Main Hall</strong>
        </div>
      </div>

      <div class="info-card">
        <div class="info-icon">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 21h18"/><path d="M5 21V7l8-4v18"/><path d="M19 21V11l-6-4"/></svg>
        </div>
        <div>
          <small>Institution</small>
          <strong>Ma'dinul Uloom Da'wa & Dars</strong>
        </div>
      </div>
    </div>
  </header>

  <!-- Main Workspace -->
  <main class="main-wrap" id="register">

    <!-- 1. PUBLIC REGISTRATION FORM -->
    <section class="glass-panel" id="registrationSection">
      <div class="panel-header">
        <div>
          <h2>Alumni Registration</h2>
          <p>Fill in your details below to generate your verified QR pass for Dec 6, 2026.</p>
        </div>
      </div>

      <form id="alumniForm" novalidate>
        <div class="photo-dropzone">
          <div class="avatar-circle">
            <svg id="avatarPlaceholder" width="34" height="34" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8">
              <path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/>
            </svg>
            <img id="avatarPreviewImg" alt="Profile Preview" />
          </div>
          <div class="upload-meta">
            <h4>Upload Your Photo <span class="req">*</span></h4>
            <p>Displayed on your official digital pass. JPG or PNG (Max 5MB).</p>
            <label for="photoInput" class="btn-choose-photo">
              <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="17 8 12 3 7 8"/><line x1="12" y1="3" x2="12" y2="15"/></svg>
              Select Photo
            </label>
            <input type="file" id="photoInput" accept="image/*" hidden />
            <div class="error-msg" id="photoError">Please upload a photo for your pass.</div>
          </div>
        </div>

        <div class="form-grid">
          <div class="form-group">
            <label for="fullName">Full Name <span class="req">*</span></label>
            <input type="text" id="fullName" class="form-control" placeholder="Enter your full name" required />
            <div class="error-msg">Please enter your full name.</div>
          </div>

          <div class="form-group">
            <label for="batchYear">Batch / Study Year <span class="req">*</span></label>
            <input type="text" id="batchYear" class="form-control" placeholder="e.g., 2016 - 2020 or 2019" required />
            <div class="error-msg">Please enter your batch year.</div>
          </div>

          <div class="form-group">
            <label for="dob">Date of Birth <span class="req">*</span></label>
            <input type="date" id="dob" class="form-control" required />
            <div class="error-msg">Please select your date of birth.</div>
          </div>

          <div class="form-group">
            <label for="location">Location (Place / District) <span class="req">*</span></label>
            <input type="text" id="location" class="form-control" placeholder="e.g., Kochannur, Thrissur" required />
            <div class="error-msg">Please enter your location.</div>
          </div>

          <div class="form-group">
            <label for="primaryPhone">Primary Phone Number <span class="req">*</span></label>
            <input type="tel" id="primaryPhone" class="form-control" placeholder="e.g., +91 98765 43210" required />
            <div class="error-msg">Please enter your phone number.</div>
          </div>

          <div class="form-group">
            <label for="secondaryPhone">WhatsApp / Alternate Number</label>
            <input type="tel" id="secondaryPhone" class="form-control" placeholder="Optional WhatsApp number" />
          </div>
        </div>

        <button type="submit" class="btn-submit" id="btnSubmitForm">
          Generate Digital Entry Pass
          <svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
        </button>
      </form>
    </section>

    <!-- 2. GENERATED DIGITAL TICKET -->
    <section class="glass-panel" id="ticketSection">
      <div class="confirmed-pill">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/></svg>
        <span id="ticketConfirmText">Registration Confirmed! Download & bring this pass on December 6, 2026.</span>
      </div>

      <div class="ticket-stage">
        <div id="digitalTicket">
          <div class="ticket-top-accent"></div>

          <div class="ticket-header">
            <div class="ticket-header-row">
              <span class="ticket-inst">MA'DINUL ULOOM DA'WA & DARS</span>
              <span class="ticket-verified">ALUMNI PASS</span>
            </div>
            <div class="ticket-title">OLD STUDENTS MEET</div>
            <div class="ticket-sub">📅 December 6, 2026 • Kochannur</div>
          </div>

          <div class="ticket-body">
            <div class="ticket-profile">
              <img id="tPhoto" class="ticket-avatar" alt="Attendee Photo" />
              <div>
                <div class="ticket-name" id="tName">Attendee Name</div>
                <span class="ticket-batch-pill" id="tBatch">Batch 2020</span>
              </div>
            </div>

            <div class="ticket-grid">
              <div class="t-field"><label>Location</label><span id="tLocation">—</span></div>
              <div class="t-field"><label>Date of Birth</label><span id="tDob">—</span></div>
              <div class="t-field"><label>Primary Phone</label><span id="tPhone1">—</span></div>
              <div class="t-field"><label>WhatsApp / Alt</label><span id="tPhone2">—</span></div>
              <div class="t-field t-field-full">
                <label>Venue & Date</label>
                <span>Ma'dinul Uloom Dars, Kochannur Main Hall • Dec 6, 2026</span>
              </div>
            </div>
          </div>

          <div class="ticket-tear">
            <div class="cutout cutout-l"></div>
            <div class="cutout cutout-r"></div>
          </div>

          <div class="ticket-qr-footer">
            <div class="qr-info">
              <div class="pass-id-lbl">Ticket Code / Reg ID</div>
              <div class="pass-id-val" id="tRegId">MUD-2026-0000</div>
              <div class="qr-note">Present this QR code or Ticket Code to the admin desk for verification.</div>
            </div>
            <div class="qr-white-box" id="qrContainer"></div>
          </div>
        </div>
      </div>

      <div class="actions-grid">
        <button type="button" class="btn-act btn-dl" id="btnDownload">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
          Download Pass (HD PNG)
        </button>
        <button type="button" class="btn-act btn-native-share" id="btnShare">Share Pass</button>
        <button type="button" class="btn-act btn-wa" id="btnWhatsApp">WhatsApp</button>
        <button type="button" class="btn-act btn-again" id="btnRegisterAnother">Register Another Alumni</button>
      </div>
    </section>

    <!-- 3. ADMIN-ONLY VERIFICATION & QR SCANNER PANEL -->
    <section class="glass-panel" id="adminPanelSection">
      <div class="panel-header">
        <div>
          <span class="admin-badge">🔒 Admin Access Only</span>
          <h2 style="margin-top:0.35rem;">Check-In & Ticket Verification</h2>
          <p>Scan attendee QR passes or enter a Ticket Code manually to verify entry.</p>
        </div>
        <button type="button" class="btn-logout" id="btnAdminLogout">Exit Admin</button>
      </div>

      <div id="syncStatusPill" class="sync-pill sync-local"></div>

      <!-- Live Stats -->
      <div class="stats-row">
        <div class="stat-card"><strong id="statTotal">0</strong><span>Registered</span></div>
        <div class="stat-card stat-green"><strong id="statCheckedIn">0</strong><span>Checked In</span></div>
        <div class="stat-card stat-gold"><strong id="statPending">0</strong><span>Pending</span></div>
      </div>

      <!-- Admin Tabs -->
      <div class="admin-tabs">
        <button type="button" class="tab-btn active" data-tab="tabScanner">📷 QR Scanner</button>
        <button type="button" class="tab-btn" data-tab="tabManual">⌨️ Enter Ticket Code</button>
        <button type="button" class="tab-btn" data-tab="tabList">📋 Attendee List</button>
      </div>

      <!-- TAB 1: LIVE CAMERA QR SCANNER -->
      <div class="tab-pane active" id="tabScanner">
        <div class="scanner-box">
          <div id="qrReader"></div>
          <div class="scanner-controls">
            <button type="button" class="btn-cam btn-cam-start" id="btnStartScan">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4"><path d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"/><circle cx="12" cy="13" r="4"/></svg>
              Start Camera Scanner
            </button>
            <button type="button" class="btn-cam btn-cam-stop" id="btnStopScan">Stop Camera</button>
          </div>
          <p style="font-size:0.76rem; color:#94a3b8; margin-top:0.75rem;">
            Point your camera at the attendee's Digital Pass QR Code. (Requires HTTPS on mobile.)
          </p>
        </div>
      </div>

      <!-- TAB 2: MANUAL TICKET CODE VERIFICATION -->
      <div class="tab-pane" id="tabManual">
        <div class="manual-box">
          <label for="manualCodeInput" style="font-size:0.86rem; font-weight:700; color:#e2e8f0;">
            Enter Ticket Code / Registration ID
          </label>
          <div class="manual-row">
            <input type="text" id="manualCodeInput" class="form-control" placeholder="e.g., MUD-2026-482193" />
            <button type="button" class="btn-verify" id="btnManualVerify">Verify Ticket</button>
          </div>
          <p style="font-size:0.76rem; color:#94a3b8; margin-top:0.65rem;">
            Type or paste the exact Registration ID printed on the attendee's ticket.
          </p>
        </div>
      </div>

      <!-- SHARED VERIFICATION RESULT CARD (Works for both QR Scan & Manual Entry) -->
      <div id="verifyResultCard"></div>

      <!-- TAB 3: LIVE ATTENDEE LIST -->
      <div class="tab-pane" id="tabList">
        <div class="table-tools">
          <input type="text" id="searchAttendee" class="form-control" placeholder="Search by name, ID, location, phone..." />
          <button type="button" class="btn-tool" id="btnRefreshList">↻ Refresh</button>
          <button type="button" class="btn-tool" id="btnExportCsv">⬇ Export CSV</button>
        </div>
        <div class="table-wrap">
          <table>
            <thead>
              <tr>
                <th>Ticket ID</th>
                <th>Name & Batch</th>
                <th>Location</th>
                <th>Phone</th>
                <th>Status</th>
              </tr>
            </thead>
            <tbody id="attendeeTableBody">
              <tr><td colspan="5" style="text-align:center; color:#94a3b8;">No registrations yet.</td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>

  </main>

  <footer>
    <div>© 2026 Ma'dinul Uloom Da'wa & Dars, Kochannur • Old Students Meet (Dec 6, 2026)</div>
  </footer>

  <!-- Admin Login Modal -->
  <div class="modal-backdrop" id="adminLoginModal">
    <div class="modal-card">
      <h3>🔒 Admin Verification</h3>
      <p>Enter the Organizer PIN to access the QR Scanner, Ticket Code Verifier, and Attendee List.</p>
      <input type="password" id="adminPinInput" class="form-control" placeholder="Enter Admin PIN" style="text-align:center; letter-spacing:0.15em; font-weight:700;" />
      <div class="error-msg" id="adminPinError" style="text-align:center; margin-top:0.5rem;">Incorrect Admin PIN.</div>
      <div class="modal-btns">
        <button type="button" class="btn-act btn-again" id="btnCancelLogin" style="grid-column:auto;">Cancel</button>
        <button type="button" class="btn-act btn-dl" id="btnConfirmLogin" style="grid-column:auto;">Unlock Panel</button>
      </div>
    </div>
  </div>

  <!-- Quick Background Picker -->
  <label for="bgFileInput" class="bg-picker-btn" title="Select stage photo as background">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="18" height="18" rx="2"/><circle cx="8.5" cy="8.5" r="1.5"/><polyline points="21 15 16 10 5 21"/></svg>
    Change BG
  </label>
  <input type="file" id="bgFileInput" accept="image/*" hidden />

  <div class="toast" id="toast"></div>

  <script>
    /* ============================================================
       CONFIGURATION — PASTE YOUR GOOGLE APPS SCRIPT WEB APP URL HERE
    ============================================================ */
    const EVENT_CONFIG = {
      institutionName: "Ma'dinul Uloom Da'wa & Dars",
      eventTitle: "OLD STUDENTS MEET",
      eventDateDisplay: "December 6, 2026",
      eventISO: "2026-12-06T09:00:00+05:30",
      eventVenue: "Ma'dinul Uloom Dars, Kochannur Main Hall",
      ticketPrefix: "MUD-2026",

      // 1. Paste your deployed Google Apps Script URL below (ends in /exec)
      //    Leave empty "" to test immediately using Local Browser Storage.
      GOOGLE_SCRIPT_URL: "",

      // 2. Must match ADMIN_PIN in your Google Apps Script (Code.gs)
      ADMIN_PIN: "MUD2026"
    };

    /* ============================================================
       LIVE COUNTDOWN TO DECEMBER 6, 2026
    ============================================================ */
    function updateCountdown() {
      const target = new Date(EVENT_CONFIG.eventISO).getTime();
      const diff = target - Date.now();
      if (diff <= 0) {
        document.getElementById('countdownBox').innerHTML =
          '<div class="cd-box" style="padding:0.6rem 1.2rem;"><strong>EVENT DAY!</strong><span>Welcome to Kochannur Main Hall</span></div>';
        return;
      }
      const d = Math.floor(diff / (1000 * 60 * 60 * 24));
      const h = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const m = Math.floor((diff / (1000 * 60)) % 60);
      const s = Math.floor((diff / 1000) % 60);
      document.getElementById('cdDays').textContent = String(d).padStart(2, '0');
      document.getElementById('cdHours').textContent = String(h).padStart(2, '0');
      document.getElementById('cdMins').textContent = String(m).padStart(2, '0');
      document.getElementById('cdSecs').textContent = String(s).padStart(2, '0');
    }
    updateCountdown();
    setInterval(updateCountdown, 1000);

    /* ============================================================
       BACKGROUND IMAGE PICKER & TOAST
    ============================================================ */
    const bgStage = document.getElementById('bgStage');
    const savedBg = localStorage.getItem('mud_custom_bg');
    if (savedBg) bgStage.style.backgroundImage = `url('${savedBg}')`;

    document.getElementById('bgFileInput').addEventListener('change', (e) => {
      const file = e.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = (ev) => {
        bgStage.style.backgroundImage = `url('${ev.target.result}')`;
        try { localStorage.setItem('mud_custom_bg', ev.target.result); } catch {}
        showToast('Background photo updated!');
      };
      reader.readAsDataURL(file);
    });

    function showToast(msg) {
      const t = document.getElementById('toast');
      t.textContent = msg;
      t.classList.add('show');
      setTimeout(() => t.classList.remove('show'), 3000);
    }

    function playBeep(success = true) {
      try {
        const ctx = new (window.AudioContext || window.webkitAudioContext)();
        const osc = ctx.createOscillator();
        const gain = ctx.createGain();
        osc.type = success ? 'sine' : 'sawtooth';
        osc.frequency.value = success ? 880 : 240;
        gain.gain.value = 0.12;
        osc.connect(gain);
        gain.connect(ctx.destination);
        osc.start();
        setTimeout(() => { osc.stop(); ctx.close(); }, success ? 140 : 280);
      } catch {}
    }

    /* ============================================================
       PHOTO UPLOAD (AUTO SQUARE CROP + SMALL THUMB FOR GOOGLE SHEET)
    ============================================================ */
    let croppedPhotoDataUrl = null;
    let photoThumbDataUrl = null;
    let currentAttendee = null;

    const photoInput = document.getElementById('photoInput');
    const avatarPreviewImg = document.getElementById('avatarPreviewImg');
    const avatarPlaceholder = document.getElementById('avatarPlaceholder');
    const photoError = document.getElementById('photoError');

    photoInput.addEventListener('change', (e) => {
      const file = e.target.files[0];
      if (!file) return;
      if (!file.type.startsWith('image/')) return showToast('Please select a valid image.');
      if (file.size > 5 * 1024 * 1024) return showToast('Photo must be under 5MB.');

      const reader = new FileReader();
      reader.onload = (ev) => {
        const img = new Image();
        img.onload = () => {
          const minSide = Math.min(img.width, img.height);
          const sx = (img.width - minSide) / 2;
          const sy = (img.height - minSide) / 2;

          // 320x320 crisp image for Digital Ticket PNG
          const c1 = document.createElement('canvas');
          c1.width = 320; c1.height = 320;
          c1.getContext('2d').drawImage(img, sx, sy, minSide, minSide, 0, 0, 320, 320);
          croppedPhotoDataUrl = c1.toDataURL('image/jpeg', 0.9);

          // 90x90 lightweight thumbnail for Google Sheet & Admin Verification
          const c2 = document.createElement('canvas');
          c2.width = 90; c2.height = 90;
          c2.getContext('2d').drawImage(img, sx, sy, minSide, minSide, 0, 0, 90, 90);
          photoThumbDataUrl = c2.toDataURL('image/jpeg', 0.55);

          avatarPreviewImg.src = croppedPhotoDataUrl;
          avatarPreviewImg.style.display = 'block';
          avatarPlaceholder.style.display = 'none';
          photoError.style.display = 'none';
        };
        img.src = ev.target.result;
      };
      reader.readAsDataURL(file);
    });

    /* ============================================================
       STORAGE LAYER (GOOGLE SHEETS + LOCAL FALLBACK)
    ============================================================ */
    const isCloudEnabled = () => Boolean(EVENT_CONFIG.GOOGLE_SCRIPT_URL && EVENT_CONFIG.GOOGLE_SCRIPT_URL.startsWith('http'));

    function getLocalRegs() {
      return JSON.parse(localStorage.getItem('mud_alumni_regs') || '[]');
    }

    function saveLocalReg(record) {
      const list = getLocalRegs();
      const idx = list.findIndex(x => x.regId.toUpperCase() === record.regId.toUpperCase());
      if (idx >= 0) list[idx] = record;
      else list.unshift(record);
      localStorage.setItem('mud_alumni_regs', JSON.stringify(list));
    }

    async function cloudPost(payload) {
      const res = await fetch(EVENT_CONFIG.GOOGLE_SCRIPT_URL, {
        method: 'POST',
        headers: { 'Content-Type': 'text/plain;charset=utf-8' },
        body: JSON.stringify(payload)
      });
      return await res.json();
    }

    async function cloudGet(params) {
      const qs = new URLSearchParams(params).toString();
      const res = await fetch(`${EVENT_CONFIG.GOOGLE_SCRIPT_URL}?${qs}`);
      return await res.json();
    }

    /* ============================================================
       REGISTRATION SUBMISSION
    ============================================================ */
    const form = document.getElementById('alumniForm');
    const registrationSection = document.getElementById('registrationSection');
    const ticketSection = document.getElementById('ticketSection');
    const adminPanelSection = document.getElementById('adminPanelSection');
    const heroSection = document.getElementById('heroSection');

    function generateTicketId() {
      const rand = Math.floor(1000 + Math.random() * 9000);
      const tail = Date.now().toString().slice(-2);
      return `${EVENT_CONFIG.ticketPrefix}-${rand}${tail}`;
    }

    function formatDate(dateStr) {
      if (!dateStr) return '—';
      const d = new Date(dateStr + 'T00:00:00');
      return isNaN(d) ? dateStr : d.toLocaleDateString('en-GB', { day: '2-digit', month: 'short', year: 'numeric' });
    }

    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      let valid = true;

      ['fullName', 'batchYear', 'dob', 'location', 'primaryPhone'].forEach((id) => {
        const input = document.getElementById(id);
        const err = input.nextElementSibling;
        if (!input.value.trim()) {
          err.style.display = 'block';
          input.style.borderColor = '#f87171';
          valid = false;
        } else {
          err.style.display = 'none';
          input.style.borderColor = 'rgba(148, 163, 184, 0.25)';
        }
      });

      if (!croppedPhotoDataUrl) {
        photoError.style.display = 'block';
        valid = false;
      }

      if (!valid) return showToast('Please complete all required fields.');

      const btn = document.getElementById('btnSubmitForm');
      const prevBtn = btn.innerHTML;
      btn.textContent = 'Saving Registration & Generating Pass...';
      btn.disabled = true;

      currentAttendee = {
        regId: generateTicketId(),
        fullName: document.getElementById('fullName').value.trim(),
        batchYear: document.getElementById('batchYear').value.trim(),
        dob: document.getElementById('dob').value,
        location: document.getElementById('location').value.trim(),
        primaryPhone: document.getElementById('primaryPhone').value.trim(),
        secondaryPhone: document.getElementById('secondaryPhone').value.trim() || 'Same as primary',
        status: 'Registered',
        checkedInAt: '',
        registeredAt: new Date().toLocaleString('en-IN'),
        photoThumb: photoThumbDataUrl || ''
      };

      // Save to Local Cache
      saveLocalReg(currentAttendee);

      // Sync to Google Sheet if URL is configured
      if (isCloudEnabled()) {
        try {
          await cloudPost({ action: 'register', ...currentAttendee });
          document.getElementById('ticketConfirmText').textContent =
            'Saved to Official Database! Download & bring this QR pass on December 6, 2026.';
        } catch (err) {
          console.error('Google Sheet sync error:', err);
          showToast('Pass generated (offline backup saved).');
        }
      }

      // Render Digital Pass
      document.getElementById('tPhoto').src = croppedPhotoDataUrl;
      document.getElementById('tName').textContent = currentAttendee.fullName;
      document.getElementById('tBatch').textContent = `Batch: ${currentAttendee.batchYear}`;
      document.getElementById('tLocation').textContent = currentAttendee.location;
      document.getElementById('tDob').textContent = formatDate(currentAttendee.dob);
      document.getElementById('tPhone1').textContent = currentAttendee.primaryPhone;
      document.getElementById('tPhone2').textContent = currentAttendee.secondaryPhone;
      document.getElementById('tRegId').textContent = currentAttendee.regId;

      const qrContainer = document.getElementById('qrContainer');
      qrContainer.innerHTML = '';
      new QRCode(qrContainer, {
        text: JSON.stringify({
          id: currentAttendee.regId,
          name: currentAttendee.fullName,
          batch: currentAttendee.batchYear,
          phone: currentAttendee.primaryPhone
        }),
        width: 190,
        height: 190,
        colorDark: "#02120c",
        colorLight: "#ffffff",
        correctLevel: QRCode.CorrectLevel.M
      });

      btn.innerHTML = prevBtn;
      btn.disabled = false;

      registrationSection.style.display = 'none';
      ticketSection.style.display = 'block';
      ticketSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
      showToast('Digital Entry Pass Ready!');
    });

    /* ============================================================
       TICKET DOWNLOAD & SHARE
    ============================================================ */
    async function renderTicketCanvas() {
      return await html2canvas(document.getElementById('digitalTicket'), {
        scale: 3,
        useCORS: true,
        backgroundColor: '#02120c'
      });
    }

    document.getElementById('btnDownload').addEventListener('click', async () => {
      const btn = document.getElementById('btnDownload');
      const prev = btn.innerHTML;
      btn.textContent = 'Preparing HD Pass...';
      btn.disabled = true;
      try {
        const canvas = await renderTicketCanvas();
        const a = document.createElement('a');
        a.download = `${currentAttendee.regId}_${currentAttendee.fullName.replace(/[^a-z0-9]/gi, '_')}.png`;
        a.href = canvas.toDataURL('image/png');
        a.click();
        showToast('Pass downloaded!');
      } catch {
        showToast('Download failed. Please retry.');
      } finally {
        btn.innerHTML = prev;
        btn.disabled = false;
      }
    });

    document.getElementById('btnShare').addEventListener('click', async () => {
      const text = `Assalamu Alaikum! Registered for ${EVENT_CONFIG.institutionName} — ${EVENT_CONFIG.eventTitle} (Dec 6, 2026).\nName: ${currentAttendee.fullName}\nTicket Code: ${currentAttendee.regId}\nVenue: ${EVENT_CONFIG.eventVenue}`;
      try {
        const canvas = await renderTicketCanvas();
        const blob = await new Promise((res) => canvas.toBlob(res, 'image/png'));
        const file = new File([blob], `${currentAttendee.regId}_Pass.png`, { type: 'image/png' });
        if (navigator.canShare && navigator.canShare({ files: [file] })) {
          await navigator.share({ title: 'Alumni Pass', text, files: [file] });
          return;
        } else if (navigator.share) {
          await navigator.share({ title: 'Alumni Pass', text });
          return;
        }
      } catch (err) {
        if (err.name === 'AbortError') return;
      }
      try {
        await navigator.clipboard.writeText(text);
        showToast('Pass details copied to clipboard!');
      } catch {
        showToast('Download the PNG pass to share.');
      }
    });

    document.getElementById('btnWhatsApp').addEventListener('click', () => {
      const msg =
        `*${EVENT_CONFIG.institutionName}*\n` +
        `✨ *${EVENT_CONFIG.eventTitle} — Digital Pass*\n\n` +
        `👤 *Name:* ${currentAttendee.fullName}\n` +
        `🎓 *Batch:* ${currentAttendee.batchYear}\n` +
        `🎟️ *Ticket Code:* ${currentAttendee.regId}\n` +
        `📅 *Date:* ${EVENT_CONFIG.eventDateDisplay}\n` +
        `📍 *Venue:* ${EVENT_CONFIG.eventVenue}`;
      window.open(`https://wa.me/?text=${encodeURIComponent(msg)}`, '_blank');
    });

    document.getElementById('btnRegisterAnother').addEventListener('click', () => {
      form.reset();
      croppedPhotoDataUrl = null;
      photoThumbDataUrl = null;
      avatarPreviewImg.style.display = 'none';
      avatarPlaceholder.style.display = 'block';
      ticketSection.style.display = 'none';
      registrationSection.style.display = 'block';
      registrationSection.scrollIntoView({ behavior: 'smooth' });
    });

    /* ============================================================
       ADMIN-ONLY PANEL LOGIC (AUTH, QR SCANNER, MANUAL CODE, G-SHEET)
    ============================================================ */
    let activeAdminPin = null;
    let adminAttendeesCache = [];
    let html5QrScanner = null;
    let isScannerRunning = false;
    let lastScannedText = '';
    let lastScanTime = 0;

    const adminModal = document.getElementById('adminLoginModal');
    const adminPinInput = document.getElementById('adminPinInput');
    const adminPinError = document.getElementById('adminPinError');

    document.getElementById('openAdminLoginBtn').addEventListener('click', () => {
      if (activeAdminPin) {
        showAdminPanel();
      } else {
        adminPinInput.value = '';
        adminPinError.style.display = 'none';
        adminModal.classList.add('open');
        setTimeout(() => adminPinInput.focus(), 100);
      }
    });

    document.getElementById('btnCancelLogin').addEventListener('click', () => {
      adminModal.classList.remove('open');
    });

    async function handleAdminLogin() {
      const entered = adminPinInput.value.trim();
      if (!entered) return;

      const btn = document.getElementById('btnConfirmLogin');
      btn.textContent = 'Checking...';
      btn.disabled = true;

      let verified = false;
      if (isCloudEnabled()) {
        try {
          const resp = await cloudGet({ action: 'login', pin: entered });
          verified = resp.ok === true;
        } catch {
          verified = entered === EVENT_CONFIG.ADMIN_PIN;
        }
      } else {
        verified = entered === EVENT_CONFIG.ADMIN_PIN;
      }

      btn.textContent = 'Unlock Panel';
      btn.disabled = false;

      if (verified) {
        activeAdminPin = entered;
        adminModal.classList.remove('open');
        showAdminPanel();
        showToast('Admin Panel Unlocked');
      } else {
        adminPinError.style.display = 'block';
        playBeep(false);
      }
    }

    document.getElementById('btnConfirmLogin').addEventListener('click', handleAdminLogin);
    adminPinInput.addEventListener('keydown', (e) => { if (e.key === 'Enter') handleAdminLogin(); });

    function showAdminPanel() {
      heroSection.style.display = 'none';
      registrationSection.style.display = 'none';
      ticketSection.style.display = 'none';
      adminPanelSection.style.display = 'block';
      window.scrollTo({ top: 0, behavior: 'smooth' });

      const syncPill = document.getElementById('syncStatusPill');
      if (isCloudEnabled()) {
        syncPill.className = 'sync-pill sync-cloud';
        syncPill.textContent = '☁️ Live Connected to Google Sheets';
      } else {
        syncPill.className = 'sync-pill sync-local';
        syncPill.textContent = '⚡ Local Test Mode (Add GOOGLE_SCRIPT_URL in code to sync Google Sheets)';
      }

      refreshAdminData();
    }

    function exitAdminPanel() {
      stopCameraScanner();
      activeAdminPin = null;
      adminPanelSection.style.display = 'none';
      heroSection.style.display = 'block';
      registrationSection.style.display = 'block';
      document.getElementById('verifyResultCard').style.display = 'none';
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    document.getElementById('btnAdminLogout').addEventListener('click', exitAdminPanel);
    document.getElementById('navHomeBtn').addEventListener('click', (e) => {
      if (adminPanelSection.style.display === 'block') {
        e.preventDefault();
        exitAdminPanel();
      }
    });

    // Admin Tab Switching
    document.querySelectorAll('.tab-btn').forEach((btn) => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        document.querySelectorAll('.tab-pane').forEach(p => p.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById(btn.dataset.tab).classList.add('active');

        if (btn.dataset.tab !== 'tabScanner') stopCameraScanner();
        if (btn.dataset.tab === 'tabList') {
          document.getElementById('verifyResultCard').style.display = 'none';
          refreshAdminData();
        }
      });
    });

    // Fetch All Attendees (Google Sheet or Local Storage)
    async function refreshAdminData() {
      if (isCloudEnabled()) {
        try {
          const resp = await cloudGet({ action: 'list', pin: activeAdminPin });
          if (resp.ok && Array.isArray(resp.attendees)) {
            adminAttendeesCache = resp.attendees;
          }
        } catch (err) {
          console.error(err);
          adminAttendeesCache = getLocalRegs();
        }
      } else {
        adminAttendeesCache = getLocalRegs();
      }
      renderAdminStatsAndTable();
    }

    function renderAdminStatsAndTable() {
      const total = adminAttendeesCache.length;
      const checked = adminAttendeesCache.filter(a => a.status === 'Checked In').length;
      document.getElementById('statTotal').textContent = total;
      document.getElementById('statCheckedIn').textContent = checked;
      document.getElementById('statPending').textContent = total - checked;

      const query = document.getElementById('searchAttendee').value.trim().toLowerCase();
      const filtered = adminAttendeesCache.filter(a =>
        !query ||
        a.regId.toLowerCase().includes(query) ||
        a.fullName.toLowerCase().includes(query) ||
        a.location.toLowerCase().includes(query) ||
        a.primaryPhone.toLowerCase().includes(query)
      );

      const tbody = document.getElementById('attendeeTableBody');
      if (!filtered.length) {
        tbody.innerHTML = '<tr><td colspan="5" style="text-align:center; color:#94a3b8;">No matching attendees found.</td></tr>';
        return;
      }

      tbody.innerHTML = filtered.map(a => `
        <tr>
          <td style="font-family:Outfit,monospace; font-weight:700; color:#fde68a;">${escapeHtml(a.regId)}</td>
          <td><strong>${escapeHtml(a.fullName)}</strong><br/><small style="color:#94a3b8;">Batch: ${escapeHtml(a.batchYear)}</small></td>
          <td>${escapeHtml(a.location)}</td>
          <td>${escapeHtml(a.primaryPhone)}</td>
          <td>
            <span class="status-chip ${a.status === 'Checked In' ? 'chip-in' : 'chip-reg'}">
              ${a.status === 'Checked In' ? '✓ Checked In' : 'Pending'}
            </span>
          </td>
        </tr>
      `).join('');
    }

    document.getElementById('searchAttendee').addEventListener('input', renderAdminStatsAndTable);
    document.getElementById('btnRefreshList').addEventListener('click', () => {
      refreshAdminData();
      showToast('List refreshed!');
    });

    // Export CSV
    document.getElementById('btnExportCsv').addEventListener('click', () => {
      if (!adminAttendeesCache.length) return showToast('No data to export.');
      const headers = ['Reg ID', 'Full Name', 'Batch', 'DOB', 'Location', 'Primary Phone', 'WhatsApp/Alt', 'Status', 'Checked In At', 'Registered At'];
      const rows = adminAttendeesCache.map(r => [
        r.regId, r.fullName, r.batchYear, r.dob, r.location, r.primaryPhone, r.secondaryPhone, r.status, r.checkedInAt, r.registeredAt
      ].map(v => `"${String(v || '').replace(/"/g, '""')}"`).join(','));
      const csv = [headers.join(','), ...rows].join('\n');
      const a = document.createElement('a');
      a.href = URL.createObjectURL(new Blob([csv], { type: 'text/csv;charset=utf-8;' }));
      a.download = `Madinul_Uloom_Dec6_Attendees.csv`;
      a.click();
      showToast('CSV exported!');
    });

    /* ============================================================
       LIVE CAMERA QR CODE SCANNER
    ============================================================ */
    const btnStartScan = document.getElementById('btnStartScan');
    const btnStopScan = document.getElementById('btnStopScan');

    async function startCameraScanner() {
      if (isScannerRunning) return;
      try {
        html5QrScanner = new Html5Qrcode("qrReader");
        await html5QrScanner.start(
          { facingMode: "environment" },
          { fps: 10, qrbox: { width: 240, height: 240 } },
          onQrDecoded
        );
        isScannerRunning = true;
        btnStartScan.style.display = 'none';
        btnStopScan.style.display = 'inline-flex';
      } catch (err) {
        console.error(err);
        showToast('Camera access denied or requires HTTPS.');
      }
    }

    async function stopCameraScanner() {
      if (!isScannerRunning || !html5QrScanner) return;
      try {
        await html5QrScanner.stop();
        html5QrScanner.clear();
      } catch {}
      isScannerRunning = false;
      btnStartScan.style.display = 'inline-flex';
      btnStopScan.style.display = 'none';
    }

    btnStartScan.addEventListener('click', startCameraScanner);
    btnStopScan.addEventListener('click', stopCameraScanner);

    function onQrDecoded(decodedText) {
      const now = Date.now();
      if (decodedText === lastScannedText && now - lastScanTime < 2800) return;
      lastScannedText = decodedText;
      lastScanTime = now;

      let ticketCode = decodedText.trim();
      try {
        const parsed = JSON.parse(decodedText);
        if (parsed && parsed.id) ticketCode = String(parsed.id).trim();
      } catch {}

      verifyTicketCode(ticketCode);
    }

    /* ============================================================
       MANUAL TICKET CODE ENTRY & SHARED VERIFICATION ENGINE
    ============================================================ */
    document.getElementById('btnManualVerify').addEventListener('click', () => {
      const code = document.getElementById('manualCodeInput').value.trim();
      if (!code) return showToast('Please enter a Ticket Code.');
      verifyTicketCode(code);
    });

    document.getElementById('manualCodeInput').addEventListener('keydown', (e) => {
      if (e.key === 'Enter') document.getElementById('btnManualVerify').click();
    });

    async function verifyTicketCode(rawCode) {
      const code = rawCode.trim().toUpperCase();
      const card = document.getElementById('verifyResultCard');
      card.style.display = 'block';
      card.className = 'res-warn';
      card.innerHTML = `<div class="res-status-title">⏳ Verifying Ticket <strong>${escapeHtml(code)}</strong>...</div>`;

      let foundAttendee = null;

      if (isCloudEnabled()) {
        try {
          const resp = await cloudGet({ action: 'verify', regId: code, pin: activeAdminPin });
          if (resp.ok && resp.found) foundAttendee = resp.attendee;
        } catch (err) {
          console.error(err);
        }
      }

      // Fallback check in local cache if not cloud-enabled
      if (!foundAttendee && !isCloudEnabled()) {
        foundAttendee = getLocalRegs().find(a => a.regId.toUpperCase() === code) || null;
      }

      if (!foundAttendee) {
        playBeep(false);
        card.className = 'res-invalid';
        card.innerHTML = `
          <div class="res-status-title" style="color:#fca5a5;">❌ INVALID / NOT FOUND</div>
          <p style="font-size:0.86rem; color:#e2e8f0;">
            No registration matches Ticket Code <strong>${escapeHtml(code)}</strong>. Please double-check the code or ask the attendee to register.
          </p>
        `;
        return;
      }

      playBeep(true);
      renderVerifiedAttendee(foundAttendee);
    }

    function renderVerifiedAttendee(a) {
      const card = document.getElementById('verifyResultCard');
      const alreadyIn = a.status === 'Checked In';

      card.className = alreadyIn ? 'res-warn' : 'res-valid';
      const thumbHtml = a.photoThumb
        ? `<img src="${a.photoThumb}" class="res-thumb" alt="Photo" />`
        : `<div class="res-thumb" style="display:flex;align-items:center;justify-content:center;font-weight:800;font-size:1.3rem;">${escapeHtml(a.fullName.charAt(0).toUpperCase())}</div>`;

      card.innerHTML = `
        <div class="res-status-title" style="color:${alreadyIn ? '#fde68a' : '#6ee7b7'};">
          ${alreadyIn ? '⚠️ ALREADY CHECKED IN' : '✅ VALID TICKET — READY TO CHECK IN'}
        </div>
        <div class="res-attendee-row">
          ${thumbHtml}
          <div>
            <div style="font-family:Outfit,sans-serif; font-size:1.2rem; font-weight:800;">${escapeHtml(a.fullName)}</div>
            <div style="font-size:0.82rem; color:#fde68a; font-weight:700;">${escapeHtml(a.regId)} • Batch: ${escapeHtml(a.batchYear)}</div>
          </div>
        </div>
        <div class="res-meta-grid">
          <div><small>Location</small>${escapeHtml(a.location)}</div>
          <div><small>Primary Phone</small>${escapeHtml(a.primaryPhone)}</div>
          <div><small>Date of Birth</small>${escapeHtml(formatDate(a.dob))}</div>
          <div><small>Status</small>${alreadyIn ? `Checked In (${escapeHtml(a.checkedInAt)})` : 'Not Checked In Yet'}</div>
        </div>
        ${alreadyIn
          ? `<div style="text-align:center; font-size:0.82rem; color:#fde68a; font-weight:700; padding:0.5rem;">This pass was already scanned at ${escapeHtml(a.checkedInAt)}.</div>`
          : `<button type="button" class="btn-checkin-now" id="btnConfirmCheckIn">✓ Mark Attendee as Checked In</button>`
        }
      `;

      const checkBtn = document.getElementById('btnConfirmCheckIn');
      if (checkBtn) {
        checkBtn.addEventListener('click', () => markAttendeeCheckedIn(a));
      }
    }

    async function markAttendeeCheckedIn(attendee) {
      const btn = document.getElementById('btnConfirmCheckIn');
      btn.textContent = 'Updating Status...';
      btn.disabled = true;

      const nowStr = new Date().toLocaleString('en-IN');

      if (isCloudEnabled()) {
        try {
          const resp = await cloudPost({
            action: 'checkin',
            regId: attendee.regId,
            pin: activeAdminPin
          });
          if (resp.ok && resp.attendee) {
            playBeep(true);
            showToast(`${attendee.fullName} Checked In!`);
            renderVerifiedAttendee(resp.attendee);
            refreshAdminData();
            return;
          } else if (resp.alreadyCheckedIn) {
            playBeep(false);
            renderVerifiedAttendee(resp.attendee);
            return;
          } else {
            showToast(resp.error || 'Check-in failed.');
            btn.disabled = false;
            btn.textContent = '✓ Mark Attendee as Checked In';
            return;
          }
        } catch (err) {
          console.error(err);
          showToast('Network error updating Google Sheet.');
          btn.disabled = false;
          btn.textContent = '✓ Mark Attendee as Checked In';
          return;
        }
      }

      // Local Mode Check-In
      const list = getLocalRegs();
      const idx = list.findIndex(x => x.regId.toUpperCase() === attendee.regId.toUpperCase());
      if (idx >= 0) {
        list[idx].status = 'Checked In';
        list[idx].checkedInAt = nowStr;
        localStorage.setItem('mud_alumni_regs', JSON.stringify(list));
        playBeep(true);
        showToast(`${attendee.fullName} Checked In!`);
        renderVerifiedAttendee(list[idx]);
        refreshAdminData();
      }
    }

    function escapeHtml(str) {
      return String(str || '').replace(/[&<>"']/g, (m) => ({
        '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;'
      }[m]));
    }
  </script>
</body>
</html>
