<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Innerly — Eliminar cuenta</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #0f1510;
      --card: #1a1f18;
      --border: #2a302a;
      --sage: #5C7A59;
      --sage-light: #7a9e77;
      --text: #ede8e0;
      --soft: #8a9088;
      --danger: #c0574a;
      --danger-bg: #2a1a18;
    }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 40px 20px;
    }

    /* Ambient orb */
    body::before {
      content: '';
      position: fixed;
      top: -120px;
      left: 50%;
      transform: translateX(-50%);
      width: 600px;
      height: 400px;
      background: radial-gradient(ellipse, rgba(92,122,89,0.12) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    .container {
      position: relative;
      z-index: 1;
      max-width: 560px;
      width: 100%;
    }

    /* Logo */
    .logo {
      text-align: center;
      margin-bottom: 36px;
    }
    .logo-icon {
      font-size: 40px;
      display: block;
      margin-bottom: 8px;
      animation: float 4s ease-in-out infinite;
    }
    .logo-name {
      font-family: 'Playfair Display', serif;
      font-size: 28px;
      font-weight: 600;
      color: var(--text);
      letter-spacing: -0.02em;
    }
    .logo-tagline {
      font-size: 13px;
      color: var(--soft);
      margin-top: 4px;
      letter-spacing: 0.04em;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    /* Card */
    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 24px;
      padding: 36px 32px;
      margin-bottom: 20px;
    }

    .card h1 {
      font-family: 'Playfair Display', serif;
      font-size: 22px;
      font-weight: 600;
      color: var(--text);
      margin-bottom: 12px;
      letter-spacing: -0.02em;
    }

    .card p {
      font-size: 14px;
      line-height: 1.7;
      color: var(--soft);
      margin-bottom: 16px;
    }

    /* Steps */
    .steps {
      list-style: none;
      margin: 20px 0 24px;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .steps li {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      font-size: 14px;
      color: var(--text);
      line-height: 1.5;
    }
    .step-num {
      flex-shrink: 0;
      width: 24px;
      height: 24px;
      border-radius: 50%;
      background: rgba(92,122,89,0.18);
      border: 1px solid var(--sage);
      color: var(--sage-light);
      font-size: 12px;
      font-weight: 500;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 1px;
    }

    /* Divider */
    .divider {
      height: 1px;
      background: var(--border);
      margin: 24px 0;
    }

    /* Warning box */
    .warning {
      background: var(--danger-bg);
      border: 1px solid rgba(192,87,74,0.3);
      border-radius: 14px;
      padding: 14px 16px;
      font-size: 13px;
      color: #e08880;
      line-height: 1.6;
      margin-bottom: 24px;
    }
    .warning strong {
      color: #e8a09a;
      font-weight: 500;
    }

    /* Data table */
    .data-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 13px;
      margin-bottom: 8px;
    }
    .data-table th {
      text-align: left;
      color: var(--soft);
      font-weight: 400;
      font-size: 11px;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      padding: 0 0 10px;
      border-bottom: 1px solid var(--border);
    }
    .data-table td {
      padding: 10px 0;
      color: var(--text);
      border-bottom: 1px solid rgba(42,48,42,0.6);
      vertical-align: top;
    }
    .data-table td:first-child { color: var(--soft); width: 44%; }
    .data-table tr:last-child td { border-bottom: none; }

    .badge {
      display: inline-block;
      padding: 2px 8px;
      border-radius: 6px;
      font-size: 11px;
      font-weight: 500;
    }
    .badge-del { background: rgba(192,87,74,0.15); color: #e08880; }
    .badge-keep { background: rgba(92,122,89,0.15); color: var(--sage-light); }

    /* Email button */
    .btn-email {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      width: 100%;
      padding: 14px;
      border-radius: 14px;
      background: var(--sage);
      color: #fff;
      font-family: 'DM Sans', sans-serif;
      font-size: 15px;
      font-weight: 500;
      text-decoration: none;
      transition: background 0.2s, transform 0.15s;
      border: none;
      cursor: pointer;
      margin-top: 8px;
    }
    .btn-email:hover {
      background: var(--sage-light);
      transform: translateY(-1px);
    }
    .btn-email:active { transform: scale(0.98); }

    /* Footer */
    .footer {
      text-align: center;
      font-size: 12px;
      color: var(--soft);
      line-height: 1.6;
    }
    .footer a { color: var(--sage-light); text-decoration: none; }
    .footer a:hover { text-decoration: underline; }

    @media (max-width: 480px) {
      .card { padding: 28px 20px; }
    }
  </style>
</head>
<body>

  <div class="container">

    <div class="logo">
      <span class="logo-icon">🌿</span>
      <div class="logo-name">Innerly</div>
      <div class="logo-tagline">Tu compañero de bienestar</div>
    </div>

    <div class="card">
      <h1>Eliminar cuenta y datos</h1>
      <p>Entendemos que puede que quieras eliminar tu cuenta de Innerly. A continuación encontrarás los pasos para hacerlo y qué ocurre con tus datos.</p>

      <div class="warning">
        <strong>⚠️ Esta acción es permanente.</strong> Una vez eliminada tu cuenta, no podrás recuperar tus datos de bienestar, hábitos, diario ni historial.
      </div>

      <p style="font-size:13px; color: var(--soft); margin-bottom:6px; font-weight:500; letter-spacing:0.03em; text-transform:uppercase;">Cómo solicitar la eliminación</p>

      <ol class="steps">
        <li>
          <span class="step-num">1</span>
          <span>Abre la app Innerly e inicia sesión con tu cuenta de Google.</span>
        </li>
        <li>
          <span class="step-num">2</span>
          <span>Ve a <strong>Ajustes → Cuenta → Eliminar cuenta</strong>.</span>
        </li>
        <li>
          <span class="step-num">3</span>
          <span>Confirma la eliminación. Tus datos se borrarán de forma permanente en un plazo de <strong>30 días</strong>.</span>
        </li>
      </ol>

      <p style="font-size:13px; color:var(--soft);">Si no puedes acceder a la app, también puedes solicitar la eliminación por correo electrónico:</p>

      <a class="btn-email" href="mailto:support@innerly.app?subject=Solicitud%20de%20eliminaci%C3%B3n%20de%20cuenta&body=Hola%2C%20quiero%20eliminar%20mi%20cuenta%20de%20Innerly.%0A%0ACorreo%20asociado%3A%20">
        ✉️ Solicitar eliminación por email
      </a>

      <div class="divider"></div>

      <p style="font-size:13px; color: var(--soft); margin-bottom:14px; font-weight:500; letter-spacing:0.03em; text-transform:uppercase;">Qué se elimina y qué se conserva</p>

      <table class="data-table">
        <thead>
          <tr>
            <th>Tipo de dato</th>
            <th>Acción</th>
            <th>Plazo</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Perfil y cuenta</td>
            <td><span class="badge badge-del">Eliminado</span></td>
            <td>30 días</td>
          </tr>
          <tr>
            <td>Hábitos y rachas</td>
            <td><span class="badge badge-del">Eliminado</span></td>
            <td>30 días</td>
          </tr>
          <tr>
            <td>Estado de ánimo, estrés y sueño</td>
            <td><span class="badge badge-del">Eliminado</span></td>
            <td>30 días</td>
          </tr>
          <tr>
            <td>Entradas del diario</td>
            <td><span class="badge badge-del">Eliminado</span></td>
            <td>30 días</td>
          </tr>
          <tr>
            <td>Registros de compra (legal)</td>
            <td><span class="badge badge-keep">Conservado</span></td>
            <td>5 años (obligación legal)</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="footer">
      <p>© 2026 Innerly</p>
    </div>

  </div>

</body>
</html>
