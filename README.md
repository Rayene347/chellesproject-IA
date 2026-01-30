# chellesproject-IA[index.html](https://github.com/user-attachments/files/24973860/index.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ChellesProject — Connexion</title>
<style>
  /* === Variables et couleurs === */
  :root {
    --primary-color: #10a37f;
    --primary-hover: #0d8c6d;
    --admin-color: #9b59b6;
    --admin-hover: #8e44ad;
    --mic-color: #e74c3c;
    --mic-hover: #c0392b;
    --examen-color: #f39c12;
    --examen-hover: #d68910;
    --warning-color: #e74c3c;
    --success-color: #2ecc71;
    --background-primary: #ffffff;
    --background-secondary: #f7f7f8;
    --background-sidebar: #202123;
    --text-primary: #353740;
    --text-secondary: #6e6e80;
    --border-color: #e5e5e5;
    --shadow: 0 0 15px rgba(0, 0, 0, 0.1);
    --radius: 8px;
  }

  /* === Reset et base === */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: var(--background-secondary);
    color: var(--text-primary);
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  /* === Page de connexion === */
  .login-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    max-width: 500px;
    padding: 20px;
  }

  .login-box {
    background-color: var(--background-primary);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    padding: 40px;
    width: 100%;
    max-width: 400px;
    border: 1px solid var(--border-color);
  }

  .login-header {
    text-align: center;
    margin-bottom: 30px;
  }

  .logo-login {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    margin-bottom: 15px;
  }

  .logo-icon {
    width: 40px;
    height: 40px;
    background-color: var(--primary-color);
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-weight: bold;
    font-size: 18px;
  }

  .logo-text {
    font-size: 24px;
    font-weight: 600;
  }

  .version {
    font-size: 14px;
    color: var(--text-secondary);
    margin-left: 5px;
  }

  .login-header h1 {
    font-size: 28px;
    margin-bottom: 10px;
    color: var(--text-primary);
  }

  .login-header p {
    color: var(--text-secondary);
    font-size: 16px;
  }

  /* === Formulaire === */
  .form-group {
    margin-bottom: 20px;
  }

  .form-group label {
    display: block;
    margin-bottom: 8px;
    font-weight: 500;
    color: var(--text-primary);
  }

  .form-group input {
    width: 100%;
    padding: 12px 16px;
    border: 1px solid var(--border-color);
    border-radius: var(--radius);
    font-size: 16px;
    background-color: var(--background-primary);
    transition: border-color 0.2s;
  }

  .form-group input:focus {
    outline: none;
    border-color: var(--primary-color);
  }

  .age-warning {
    color: #ff6b6b;
    font-size: 14px;
    margin-top: 5px;
    display: none;
  }

  .login-button {
    width: 100%;
    padding: 14px;
    background-color: var(--primary-color);
    color: white;
    border: none;
    border-radius: var(--radius);
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
    transition: background-color 0.2s;
    margin-top: 10px;
  }

  .login-button:hover {
    background-color: var(--primary-hover);
  }

  /* === Message d'erreur === */
  .error-message {
    background-color: #ffebee;
    color: #d32f2f;
    padding: 12px;
    border-radius: var(--radius);
    margin-top: 20px;
    text-align: center;
    display: none;
    border: 1px solid #ffcdd2;
  }

  /* === Pied de page === */
  .login-footer {
    margin-top: 30px;
    text-align: center;
    color: var(--text-secondary);
    font-size: 14px;
  }

  /* === Page chatbot (cachée initialement) === */
  .chat-page, .quiz-page, .admin-page, .examen-page {
    display: none;
    width: 100%;
    height: 100vh;
    flex-direction: column;
  }

  /* === Page historique === */
  .history-modal, .admin-modal, .courses-modal, .examen-modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    z-index: 1000;
    justify-content: center;
    align-items: center;
  }

  .history-content, .admin-content, .courses-content, .examen-content {
    background: white;
    width: 90%;
    max-width: 1000px;
    max-height: 90vh;
    border-radius: var(--radius);
    padding: 30px;
    overflow-y: auto;
    box-shadow: var(--shadow);
  }

  /* === STYLES POUR LE SYSTÈME D'EXAMEN === */
  .examen-header {
    text-align: center;
    margin-bottom: 30px;
    padding-bottom: 20px;
    border-bottom: 2px solid var(--examen-color);
  }

  .examen-timer {
    position: fixed;
    top: 20px;
    right: 20px;
    background: var(--examen-color);
    color: white;
    padding: 15px 25px;
    border-radius: var(--radius);
    font-size: 24px;
    font-weight: bold;
    z-index: 1000;
    box-shadow: var(--shadow);
  }

  .timer-warning {
    background: var(--warning-color) !important;
    animation: pulse 1s infinite;
  }

  @keyframes pulse {
    0% { opacity: 1; }
    50% { opacity: 0.7; }
    100% { opacity: 1; }
  }

  .examen-content {
    padding: 20px;
    max-width: 900px;
    margin: 0 auto;
  }

  .examen-question {
    background: var(--background-primary);
    padding: 25px;
    border-radius: var(--radius);
    margin-bottom: 25px;
    box-shadow: var(--shadow);
    border: 2px solid var(--border-color);
  }

  .examen-question-number {
    font-size: 14px;
    color: var(--text-secondary);
    margin-bottom: 10px;
  }

  .examen-options {
    display: grid;
    gap: 12px;
    margin: 20px 0;
  }

  .examen-option {
    padding: 15px;
    background: var(--background-secondary);
    border: 2px solid var(--border-color);
    border-radius: var(--radius);
    cursor: pointer;
    transition: all 0.2s;
    text-align: left;
    font-size: 16px;
  }

  .examen-option:hover {
    background: #f0f0f0;
  }

  .examen-option.selected {
    border-color: var(--examen-color);
    background: rgba(243, 156, 18, 0.1);
  }

  .examen-navigation {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
  }

  .examen-btn {
    padding: 12px 30px;
    background: var(--examen-color);
    color: white;
    border: none;
    border-radius: var(--radius);
    cursor: pointer;
    font-weight: 600;
    transition: background 0.2s;
  }

  .examen-btn:hover {
    background: var(--examen-hover);
  }

  .examen-btn.secondary {
    background: var(--background-secondary);
    color: var(--text-primary);
    border: 1px solid var(--border-color);
  }

  .examen-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }

  .examen-results {
    text-align: center;
    padding: 40px;
  }

  .badge-earned {
    width: 150px;
    height: 150px;
    margin: 0 auto 30px;
    background: linear-gradient(135deg, var(--examen-color), var(--examen-hover));
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 14px;
    font-weight: bold;
    box-shadow: 0 10px 30px rgba(243, 156, 18, 0.3);
  }

  .badge-earned .badge-icon {
    font-size: 48px;
    margin-bottom: 10px;
  }

  .cheating-warning {
    position: fixed;
    top: 20px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--warning-color);
    color: white;
    padding: 15px 30px;
    border-radius: var(--radius);
    font-weight: bold;
    z-index: 2000;
    animation: slideIn 0.3s ease;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  }

  @keyframes slideIn {
    from { transform: translate(-50%, -100%); }
    to { transform: translate(-50%, 0); }
  }

  .examen-progress {
    margin: 20px 0;
    text-align: center;
  }

  .progress-bar {
    height: 8px;
    background: var(--border-color);
    border-radius: 4px;
    overflow: hidden;
    margin-top: 10px;
  }

  .progress-fill {
    height: 100%;
    background: var(--examen-color);
    transition: width 0.3s ease;
  }

  .security-indicator {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: rgba(46, 204, 113, 0.9);
    color: white;
    padding: 10px 15px;
    border-radius: var(--radius);
    font-size: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
    z-index: 1000;
  }

  .security-indicator.warning {
    background: rgba(231, 76, 60, 0.9);
  }

  /* === Page quiz === */
  .quiz-content {
    padding: 30px;
    max-width: 800px;
    margin: 0 auto;
    height: 100%;
    overflow-y: auto;
  }

  .quiz-header {
    text-align: center;
    margin-bottom: 30px;
    padding-bottom: 20px;
    border-bottom: 2px solid var(--primary-color);
  }

  .quiz-progress {
    background: var(--background-secondary);
    padding: 10px;
    border-radius: var(--radius);
    margin: 20px 0;
    text-align: center;
  }

  .quiz-question {
    background: var(--background-primary);
    padding: 25px;
    border-radius: var(--radius);
    margin-bottom: 25px;
    box-shadow: var(--shadow);
    border: 1px solid var(--border-color);
  }

  .quiz-options {
    display: grid;
    gap: 12px;
    margin: 20px 0;
  }

  .quiz-option {
    padding: 15px;
    background: var(--background-secondary);
    border: 2px solid var(--border-color);
    border-radius: var(--radius);
    cursor: pointer;
    transition: all 0.2s;
    text-align: left;
    font-size: 16px;
  }

  .quiz-option:hover {
    background: #f0f0f0;
  }

  .quiz-option.selected {
    border-color: var(--primary-color);
    background: rgba(16, 163, 127, 0.1);
  }

  .quiz-option.correct {
    border-color: #4CAF50;
    background: rgba(76, 175, 80, 0.1);
  }

  .quiz-option.incorrect {
    border-color: #f44336;
    background: rgba(244, 67, 54, 0.1);
  }

  .quiz-navigation {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
  }

  .quiz-btn {
    padding: 12px 30px;
    background: var(--primary-color);
    color: white;
    border: none;
    border-radius: var(--radius);
    cursor: pointer;
    font-weight: 600;
    transition: background 0.2s;
  }

  .quiz-btn:hover {
    background: var(--primary-hover);
  }

  .quiz-btn.secondary {
    background: var(--background-secondary);
    color: var(--text-primary);
    border: 1px solid var(--border-color);
  }

  .quiz-results {
    text-align: center;
    padding: 40px;
  }

  .score-circle {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    background: var(--primary-color);
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 0 auto 30px;
    font-size: 24px;
    font-weight: bold;
  }

  .score-text {
    font-size: 18px;
    margin-bottom: 20px;
  }

  .back-to-chat-btn {
    background: var(--primary-color);
    color: white;
    border: none;
    padding: 12px 30px;
    border-radius: var(--radius);
    cursor: pointer;
    font-size: 16px;
    margin-top: 20px;
  }

  /* === STYLES POUR L'ESPACE ADMIN === */
  .admin-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
    padding-bottom: 20px;
    border-bottom: 2px solid var(--admin-color);
  }

  .admin-stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
    margin-bottom: 30px;
  }

  .stat-card {
    background: white;
    padding: 20px;
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    text-align: center;
    border-top: 4px solid var(--admin-color);
  }

  .stat-value {
    font-size: 32px;
    font-weight: bold;
    color: var(--admin-color);
    margin: 10px 0;
  }

  .stat-label {
    color: var(--text-secondary);
    font-size: 14px;
  }

  /* CHARTES RÉDUITES */
  .charts-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin: 20px 0;
  }

  .chart-box {
    background: white;
    padding: 15px;
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    height: 200px;
  }

  .chart-title {
    text-align: center;
    margin-bottom: 10px;
    color: var(--text-primary);
    font-size: 16px;
    font-weight: 600;
  }

  .chart-canvas {
    width: 100% !important;
    height: 150px !important;
  }

  .admin-actions {
    display: flex;
    gap: 15px;
    justify-content: center;
    margin-top: 30px;
    padding-top: 20px;
    border-top: 1px solid var(--border-color);
  }

  .admin-action-btn {
    padding: 12px 24px;
    border: none;
    border-radius: var(--radius);
    cursor: pointer;
    font-weight: 600;
    transition: all 0.2s;
  }

  .admin-action-btn.export {
    background: var(--admin-color);
    color: white;
  }

  .admin-action-btn.export:hover {
    background: var(--admin-hover);
  }

  .admin-action-btn.reset {
    background: #ffebee;
    color: #d32f2f;
    border: 1px solid #ffcdd2;
  }

  .admin-action-btn.reset:hover {
    background: #ffcdd2;
  }

  .password-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 40px;
    text-align: center;
  }

  .password-input {
    width: 100%;
    padding: 15px;
    margin: 20px 0;
    border: 2px solid var(--border-color);
    border-radius: var(--radius);
    font-size: 16px;
    text-align: center;
    letter-spacing: 2px;
  }

  .password-input:focus {
    border-color: var(--admin-color);
    outline: none;
  }

  .password-submit {
    width: 100%;
    padding: 15px;
    background: var(--admin-color);
    color: white;
    border: none;
    border-radius: var(--radius);
    font-size: 16px;
    font-weight: 600;
    cursor: pointer;
  }

  .password-submit:hover {
    background: var(--admin-hover);
  }

  .password-error {
    color: #d32f2f;
    margin-top: 10px;
    display: none;
  }

  .users-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
    font-size: 14px;
  }

  .users-table th,
  .users-table td {
    padding: 10px;
    text-align: left;
    border-bottom: 1px solid var(--border-color);
  }

  .users-table th {
    background: var(--background-secondary);
    font-weight: 600;
    font-size: 13px;
  }

  .users-table tr:hover {
    background: var(--background-secondary);
  }

  /* === NOUVEAUX STYLES POUR LE SYSTÈME DE NIVEAUX === */
  .levels-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
    margin: 20px 0;
  }

  .level-card {
    background: white;
    padding: 20px;
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    text-align: center;
    border: 2px solid var(--border-color);
    transition: transform 0.2s;
  }

  .level-card.current {
    border-color: var(--primary-color);
    background: rgba(16, 163, 127, 0.05);
  }

  .level-card.locked {
    opacity: 0.6;
  }

  .level-card:hover {
    transform: translateY(-5px);
  }

  .level-icon {
    font-size: 32px;
    margin-bottom: 10px;
  }

  .level-name {
    font-weight: bold;
    margin-bottom: 5px;
    color: var(--text-primary);
  }

  .level-xp {
    font-size: 14px;
    color: var(--text-secondary);
  }

  /* === QUIZ SELECTION === */
  .quiz-selection-container {
    display: flex;
    flex-direction: column;
    gap: 20px;
    max-width: 800px;
    margin: 0 auto;
  }

  .quiz-category {
    background: white;
    border-radius: var(--radius);
    padding: 25px;
    box-shadow: var(--shadow);
    border: 1px solid var(--border-color);
  }

  .category-header {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 20px;
    padding-bottom: 15px;
    border-bottom: 2px solid var(--primary-color);
  }

  .category-icon {
    font-size: 32px;
    width: 60px;
    height: 60px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }

  .category-title {
    font-size: 24px;
    font-weight: 600;
    color: var(--text-primary);
  }

  .category-description {
    color: var(--text-secondary);
    margin-bottom: 20px;
  }

  .difficulty-levels {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
  }

  .difficulty-btn {
    padding: 15px;
    border: 2px solid var(--border-color);
    border-radius: var(--radius);
    background: var(--background-secondary);
    cursor: pointer;
    transition: all 0.2s;
    text-align: center;
  }

  .difficulty-btn:hover {
    background: #f0f0f0;
    transform: translateY(-2px);
  }

  .difficulty-btn.beginner {
    border-color: #4CAF50;
  }

  .difficulty-btn.intermediate {
    border-color: #FF9800;
  }

  .difficulty-btn.advanced {
    border-color: #F44336;
  }

  .difficulty-name {
    font-weight: bold;
    margin-bottom: 5px;
  }

  .difficulty-xp {
    font-size: 12px;
    color: var(--text-secondary);
  }

  /* === STYLES POUR LES COURS === */
  .courses-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
    padding-bottom: 15px;
    border-bottom: 2px solid var(--primary-color);
  }

  .courses-header h2 {
    color: var(--text-primary);
  }

  .close-courses-btn {
    background: none;
    border: none;
    font-size: 28px;
    cursor: pointer;
    color: var(--text-secondary);
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    transition: all 0.2s;
  }

  .close-courses-btn:hover {
    background: var(--background-secondary);
    color: var(--text-primary);
  }

  .courses-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    margin: 25px 0;
  }

  .course-card {
    background: white;
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: var(--shadow);
    border: 1px solid var(--border-color);
    transition: transform 0.3s, box-shadow 0.3s;
  }

  .course-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  }

  .course-header {
    padding: 25px;
    background: linear-gradient(135deg, var(--primary-color), var(--primary-hover));
    color: white;
    text-align: center;
  }

  .course-icon {
    font-size: 48px;
    margin-bottom: 15px;
  }

  .course-title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 10px;
  }

  .course-description {
    font-size: 14px;
    opacity: 0.9;
  }

  .course-content {
    padding: 25px;
    max-height: 300px;
    overflow-y: auto;
  }

  .course-section {
    margin-bottom: 20px;
    padding-bottom: 15px;
    border-bottom: 1px dashed var(--border-color);
  }

  .course-section h4 {
    color: var(--primary-color);
    margin-bottom: 10px;
    font-size: 18px;
  }

  .course-section p {
    color: var(--text-secondary);
    line-height: 1.6;
    margin-bottom: 10px;
  }

  .course-section ul {
    padding-left: 20px;
    color: var(--text-secondary);
  }

  .course-section li {
    margin-bottom: 8px;
    line-height: 1.5;
  }

  .course-actions {
    padding: 20px;
    background: var(--background-secondary);
    text-align: center;
    border-top: 1px solid var(--border-color);
  }

  .download-btn {
    padding: 12px 30px;
    background: var(--primary-color);
    color: white;
    border: none;
    border-radius: var(--radius);
    cursor: pointer;
    font-weight: 600;
    font-size: 16px;
    transition: background 0.2s;
    display: inline-flex;
    align-items: center;
    gap: 10px;
  }

  .download-btn:hover {
    background: var(--primary-hover);
  }

  .courses-intro {
    text-align: center;
    margin-bottom: 30px;
    color: var(--text-secondary);
    line-height: 1.6;
  }

  @media (max-width: 768px) {
    .charts-container {
      grid-template-columns: 1fr;
    }
    
    .admin-stats-grid {
      grid-template-columns: 1fr 1fr;
    }
    
    .admin-content, .courses-content {
      width: 95%;
      padding: 20px;
    }
    
    .chart-box {
      height: 180px;
    }
    
    .chart-canvas {
      height: 130px !important;
    }
    
    .difficulty-levels {
      grid-template-columns: 1fr;
    }
    
    .courses-grid {
      grid-template-columns: 1fr;
    }
    
    .course-content {
      max-height: 250px;
    }
    
    .examen-timer {
      top: 10px;
      right: 10px;
      padding: 10px 15px;
      font-size: 18px;
    }
  }

  @media (max-width: 480px) {
    .admin-stats-grid {
      grid-template-columns: 1fr;
    }
    
    .admin-actions {
      flex-direction: column;
    }
    
    .course-header {
      padding: 20px;
    }
    
    .course-title {
      font-size: 20px;
    }
    
    .examen-timer {
      font-size: 16px;
      padding: 8px 12px;
    }
  }
</style>
</head>
<body>
  <!-- Page de connexion -->
  <div class="login-container" id="loginPage">
    <div class="login-box">
      <div class="login-header">
        <div class="logo-login">
          <div class="logo-icon">CP</div>
          <div class="logo-text">Chelles Project<span class="version">v2.0</span></div>
        </div>
        <h1>Bienvenue</h1>
        <p>Veuillez vous connecter pour accéder à l'assistant</p>
      </div>
      
      <form id="loginForm">
        <div class="form-group">
          <label for="firstName">Prénom *</label>
          <input type="text" id="firstName" placeholder="Votre prénom" required>
        </div>
        
        <div class="form-group">
          <label for="lastName">Nom *</label>
          <input type="text" id="lastName" placeholder="Votre nom" required>
        </div>
        
        <div class="form-group">
          <label for="age">Âge *</label>
          <input type="number" id="age" placeholder="Votre âge" min="1" max="120" required>
          <div class="age-warning" id="ageWarning">
            ⚠️ Vous devez avoir plus de 14 ans pour accéder au chatbot.
          </div>
        </div>
        
        <button type="submit" class="login-button">Accéder au Chatbot</button>
      </form>
      
      <div class="error-message" id="errorMessage">
        Veuillez remplir tous les champs correctement.
      </div>
      
      <div class="login-footer">
        <p>Vos informations sont stockées localement et ne sont pas envoyées à un serveur.</p>
      </div>
    </div>
  </div>

  <!-- Page du chatbot (cachée initialement) -->
  <div class="chat-page" id="chatPage">
    <header>
      <div class="logo">
        <div class="logo-icon">CP</div>
        <div class="logo-text">Chelles Project<span class="version">v2.0</span></div>
      </div>
      <div class="header-right">
        <div class="user-info">
          <span>Connecté en tant que: <span id="userDisplay"></span></span>
        </div>
        <div class="header-buttons">
          <button class="history-btn" id="historyBtn" title="Voir l'historique">
            <span>📊</span> Historique
          </button>
          <button class="quiz-btn-header" id="startQuizBtn" title="Commencer un quiz">
            <span>📝</span> Quiz
          </button>
          <button class="courses-btn-header" id="coursesBtn" title="Accéder aux cours">
            <span>📚</span> Cours
          </button>
          <!-- NOUVEAU BOUTON EXAMEN -->
          <button class="examen-btn-header" id="startExamenBtn" title="Commencer l'examen">
            <span>📋</span> Examen
          </button>
          <button class="admin-btn" id="adminBtn" title="Espace administrateur">
            <span>🔐</span> Admin
          </button>
          <button class="logout-btn" id="logoutBtn">
            <span>🚪</span> Déconnexion
          </button>
        </div>
      </div>
    </header>
    
    <div class="main-container">
      <div class="sidebar">
        <button class="new-chat-btn" id="newChatBtn">
          <span>+</span> Nouvelle conversation
        </button>
        
        <div class="history-section">
          <div class="history-title">Aujourd'hui</div>
          <div class="history-item">
            <span>Questions sur les réseaux</span>
          </div>
          <div class="history-item">
            <span>Conseils en cybersécurité</span>
          </div>
          
          <div class="history-title">Hier</div>
          <div class="history-item">
            <span>Explications sur le cloud</span>
          </div>
          <div class="history-item">
            <span>Concepts de data science</span>
          </div>
        </div>
      </div>
      
      <div class="chat-container">
        <div class="chat-header">
          <h1>Chelles Project</h1>
          <p>Comment puis-je vous aider aujourd'hui ?</p>
        </div>
        
        <div class="chat-messages" id="chatMessages">
          <div class="message bot">
            <div class="avatar bot-avatar">CP</div>
            <div class="message-content">
              👋 Salut <span id="userFirstName"></span> ! Je suis <strong>Chelles Project</strong>, ton assistant d'informatique. Pose-moi une question sur les réseaux, le matériel, la sécurité ou la programmation.
            </div>
          </div>
          
          <div class="suggestions">
            <div class="suggestion-card">
              <h3>Explique-moi les réseaux</h3>
              <p>Concepts fondamentaux et protocoles</p>
            </div>
            <div class="suggestion-card">
              <h3>Conseils en cybersécurité</h3>
              <p>Protection et bonnes pratiques</p>
            </div>
            <div class="suggestion-card">
              <h3>Concepts de cloud</h3>
              <p>Services et déploiement</p>
            </div>
            <div class="suggestion-card">
              <h3>Data Science</h3>
              <p>Analyse et machine learning</p>
            </div>
          </div>
        </div>
        
        <div class="chat-input-container">
          <div class="chat-input-wrapper">
            <textarea class="chat-input" id="chatInput" placeholder="Message Chelles Project..."></textarea>
            <div style="position: absolute; right: 12px; bottom: 12px; display: flex; gap: 8px;">
              <button class="mic-button" id="micButton" title="Parler au microphone">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 1C10.3431 1 9 2.34315 9 4V12C9 13.6569 10.3431 15 12 15C13.6569 15 15 13.6569 15 12V4C15 2.34315 13.6569 1 12 1Z" fill="currentColor"/>
                  <path d="M5 12C5 15.866 8.13401 19 12 19C15.866 19 19 15.866 19 12M12 19V23M8 23H16" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </button>
              <button class="send-button" id="sendButton">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M22 2L11 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M22 2L15 22L11 13L2 9L22 2Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </button>
            </div>
          </div>
          <div id="recordingIndicator" style="display: none; text-align: center; margin-top: 10px;">
            <div style="display: inline-flex; align-items: center; background: #ffebee; padding: 8px 16px; border-radius: 20px; color: #d32f2f;">
              <div style="width: 10px; height: 10px; background: #d32f2f; border-radius: 50%; margin-right: 8px; animation: pulse 1.5s infinite;"></div>
              <span>Enregistrement en cours... Parlez maintenant</span>
              <button id="stopRecording" style="margin-left: 12px; background: none; border: none; color: #d32f2f; cursor: pointer;">Arrêter</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <footer>
      <p>Connecté en tant que <span id="footerUserName"></span> • Âge: <span id="footerUserAge"></span> ans • Chelles Project © 2024</p>
    </footer>
  </div>

  <!-- Page Quiz (cachée initialement) -->
  <div class="chat-page quiz-page" id="quizPage">
    <header>
      <div class="logo">
        <div class="logo-icon">CP</div>
        <div class="logo-text">Quiz Informatique<span class="version">v2.0</span></div>
      </div>
      <button class="back-to-chat-btn" id="backToChatBtn">
        <span>←</span> Retour au Chat
      </button>
    </header>
    
    <div class="quiz-content" id="quizContent">
      <!-- Le contenu du quiz sera généré ici -->
    </div>
  </div>

  <!-- Page Examen (NOUVELLE PAGE) -->
  <div class="chat-page examen-page" id="examenPage">
    <header>
      <div class="logo">
        <div class="logo-icon">CP</div>
        <div class="logo-text">Examen Certifiant<span class="version">v2.0</span></div>
      </div>
      <button class="back-to-chat-btn" id="backFromExamenBtn">
        <span>←</span> Retour au Chat
      </button>
    </header>
    
    <div class="examen-content" id="examenContent">
      <!-- Le contenu de l'examen sera généré ici -->
    </div>
    
    <div id="securityIndicator" class="security-indicator">
      <span>🔒</span> <span>Sécurité active</span>
    </div>
  </div>

  <!-- Modal Historique -->
  <div class="history-modal" id="historyModal">
    <div class="history-content">
      <div class="history-header">
        <h2>📊 Historique Complet</h2>
        <button class="close-history-btn" id="closeHistoryBtn">×</button>
      </div>
      <div class="history-list" id="historyList">
        <!-- L'historique sera affiché ici -->
      </div>
      <div class="history-actions">
        <button class="clear-history-btn" id="clearHistoryBtn">🗑️ Effacer l'historique</button>
        <button class="export-history-btn" id="exportHistoryBtn">📤 Exporter en CSV</button>
      </div>
    </div>
  </div>

  <!-- Modal Admin -->
  <div class="admin-modal" id="adminModal">
    <div class="admin-content" id="adminContent">
      <!-- Le contenu de l'admin sera généré ici -->
    </div>
  </div>

  <!-- Modal Cours -->
  <div class="courses-modal" id="coursesModal">
    <div class="courses-content" id="coursesContent">
      <!-- Le contenu des cours sera généré ici -->
    </div>
  </div>

  <style id="chatbotStyle">
    /* === Variables et couleurs === */
    :root {
      --primary-color: #10a37f;
      --primary-hover: #0d8c6d;
      --admin-color: #9b59b6;
      --admin-hover: #8e44ad;
      --mic-color: #e74c3c;
      --mic-hover: #c0392b;
      --examen-color: #f39c12;
      --examen-hover: #d68910;
      --background-primary: #ffffff;
      --background-secondary: #f7f7f8;
      --background-sidebar: #202123;
      --text-primary: #353740;
      --text-secondary: #6e6e80;
      --border-color: #e5e5e5;
      --shadow: 0 0 15px rgba(0, 0, 0, 0.1);
      --radius: 8px;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: var(--background-secondary);
      color: var(--text-primary);
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      background-color: var(--background-primary);
      padding: 12px 20px;
      border-bottom: 1px solid var(--border-color);
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .logo-icon {
      width: 24px;
      height: 24px;
      background-color: var(--primary-color);
      border-radius: 4px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: bold;
      font-size: 12px;
    }

    .logo-text {
      font-size: 18px;
      font-weight: 600;
    }

    .version {
      font-size: 12px;
      color: var(--text-secondary);
      margin-left: 5px;
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 20px;
    }

    .user-info {
      color: var(--text-secondary);
      font-size: 14px;
    }

    .header-buttons {
      display: flex;
      gap: 10px;
      align-items: center;
    }

    .history-btn, .quiz-btn-header, .courses-btn-header, .examen-btn-header, .admin-btn {
      background-color: transparent;
      color: var(--text-secondary);
      border: 1px solid var(--border-color);
      border-radius: var(--radius);
      padding: 8px 16px;
      font-size: 14px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: all 0.2s;
    }

    .history-btn:hover {
      background-color: rgba(16, 163, 127, 0.1);
      color: var(--primary-color);
      border-color: var(--primary-color);
    }

    .quiz-btn-header:hover {
      background-color: rgba(255, 193, 7, 0.1);
      color: #ff9800;
      border-color: #ff9800;
    }

    .courses-btn-header:hover {
      background-color: rgba(255, 87, 34, 0.1);
      color: #ff5722;
      border-color: #ff5722;
    }

    .examen-btn-header:hover {
      background-color: rgba(243, 156, 18, 0.1);
      color: var(--examen-color);
      border-color: var(--examen-color);
    }

    .admin-btn:hover {
      background-color: rgba(155, 89, 182, 0.1);
      color: var(--admin-color);
      border-color: var(--admin-color);
    }

    .logout-btn {
      background-color: transparent;
      color: var(--text-secondary);
      border: 1px solid var(--border-color);
      border-radius: var(--radius);
      padding: 8px 16px;
      font-size: 14px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: all 0.2s;
    }

    .logout-btn:hover {
      background-color: #ffebee;
      color: #d32f2f;
      border-color: #ffcdd2;
    }

    .mic-button {
      background: none;
      border: none;
      color: var(--mic-color);
      cursor: pointer;
      font-size: 16px;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 36px;
      height: 36px;
      border-radius: 50%;
      transition: all 0.2s;
      padding: 0;
    }

    .mic-button:hover {
      background-color: rgba(231, 76, 60, 0.1);
      color: var(--mic-hover);
    }

    .mic-button.recording {
      background-color: var(--mic-color);
      color: white;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0% { opacity: 1; }
      50% { opacity: 0.5; }
      100% { opacity: 1; }
    }

    .history-header, .courses-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 25px;
      padding-bottom: 15px;
      border-bottom: 2px solid var(--primary-color);
    }

    .history-header h2, .courses-header h2 {
      color: var(--text-primary);
    }

    .close-history-btn, .close-courses-btn {
      background: none;
      border: none;
      font-size: 28px;
      cursor: pointer;
      color: var(--text-secondary);
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 50%;
      transition: all 0.2s;
    }

    .close-history-btn:hover, .close-courses-btn:hover {
      background: var(--background-secondary);
      color: var(--text-primary);
    }

    .history-list {
      max-height: 60vh;
      overflow-y: auto;
      padding: 10px;
      margin-bottom: 20px;
    }

    .history-item-full {
      background: var(--background-secondary);
      padding: 15px;
      margin-bottom: 15px;
      border-radius: var(--radius);
      border: 1px solid var(--border-color);
    }

    .history-item-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
      font-size: 14px;
      color: var(--text-secondary);
    }

    .history-user-message {
      background: rgba(16, 163, 127, 0.1);
      padding: 12px;
      border-radius: var(--radius);
      margin-bottom: 10px;
      border-left: 4px solid var(--primary-color);
    }

    .history-bot-message {
      background: var(--background-primary);
      padding: 12px;
      border-radius: var(--radius);
      border-left: 4px solid #5436da;
    }

    .history-actions {
      display: flex;
      gap: 15px;
      justify-content: center;
      margin-top: 20px;
    }

    .clear-history-btn, .export-history-btn {
      padding: 10px 20px;
      border: none;
      border-radius: var(--radius);
      cursor: pointer;
      font-weight: 500;
      transition: all 0.2s;
    }

    .clear-history-btn {
      background: #ffebee;
      color: #d32f2f;
      border: 1px solid #ffcdd2;
    }

    .clear-history-btn:hover {
      background: #ffcdd2;
    }

    .export-history-btn {
      background: var(--primary-color);
      color: white;
    }

    .export-history-btn:hover {
      background: var(--primary-hover);
    }

    .back-to-chat-btn {
      background-color: transparent;
      color: var(--text-secondary);
      border: 1px solid var(--border-color);
      border-radius: var(--radius);
      padding: 8px 20px;
      font-size: 14px;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: all 0.2s;
    }

    .back-to-chat-btn:hover {
      background-color: rgba(16, 163, 127, 0.1);
      color: var(--primary-color);
      border-color: var(--primary-color);
    }

    .main-container {
      display: flex;
      flex: 1;
      overflow: hidden;
    }

    .sidebar {
      width: 260px;
      background-color: var(--background-sidebar);
      color: white;
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }

    .new-chat-btn {
      background-color: transparent;
      color: white;
      border: 1px solid rgba(255, 255, 255, 0.2);
      padding: 12px;
      margin: 10px;
      border-radius: var(--radius);
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 14px;
      transition: background-color 0.2s;
    }

    .new-chat-btn:hover {
      background-color: rgba(255, 255, 255, 0.1);
    }

    .history-section {
      margin-top: 10px;
      overflow-y: auto;
      flex: 1;
    }

    .history-title {
      font-size: 12px;
      color: #8e8ea0;
      padding: 10px 20px 5px;
    }

    .history-item {
      padding: 10px 20px;
      cursor: pointer;
      font-size: 14px;
      display: flex;
      align-items: center;
      gap: 10px;
      transition: background-color 0.2s;
    }

    .history-item:hover {
      background-color: rgba(255, 255, 255, 0.05);
    }

    .chat-container {
      flex: 1;
      display: flex;
      flex-direction: column;
      overflow: hidden;
    }

    .chat-header {
      padding: 20px;
      text-align: center;
      background-color: var(--background-primary);
      border-bottom: 1px solid var(--border-color);
    }

    .chat-header h1 {
      font-size: 32px;
      font-weight: 600;
      margin-bottom: 10px;
    }

    .chat-header p {
      color: var(--text-secondary);
      font-size: 16px;
    }

    .chat-messages {
      flex: 1;
      overflow-y: auto;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 24px;
      background-color: var(--background-primary);
    }

    .message {
      display: flex;
      gap: 20px;
      max-width: 800px;
      margin: 0 auto;
      width: 100%;
    }

    .user-message {
      flex-direction: row-reverse;
    }

    .avatar {
      width: 30px;
      height: 30px;
      border-radius: 4px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      flex-shrink: 0;
    }

    .user-avatar {
      background-color: #5436da;
      color: white;
    }

    .bot-avatar {
      background-color: var(--primary-color);
      color: white;
    }

    .message-content {
      background-color: var(--background-secondary);
      padding: 16px 20px;
      border-radius: var(--radius);
      line-height: 1.5;
      box-shadow: var(--shadow);
    }

    .user-message .message-content {
      background-color: var(--primary-color);
      color: white;
    }

    .suggestions {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 15px;
      max-width: 800px;
      margin: 0 auto;
      width: 100%;
    }

    .suggestion-card {
      background-color: var(--background-secondary);
      border: 1px solid var(--border-color);
      border-radius: var(--radius);
      padding: 20px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .suggestion-card:hover {
      background-color: #f0f0f0;
      box-shadow: var(--shadow);
    }

    .suggestion-card h3 {
      font-size: 16px;
      margin-bottom: 8px;
      color: var(--text-primary);
    }

    .suggestion-card p {
      color: var(--text-secondary);
      font-size: 14px;
    }

    .chat-input-container {
      padding: 20px;
      border-top: 1px solid var(--border-color);
      background-color: var(--background-primary);
    }

    .chat-input-wrapper {
      max-width: 800px;
      margin: 0 auto;
      position: relative;
    }

    .chat-input {
      width: 100%;
      padding: 12px 100px 12px 16px;
      border: 1px solid var(--border-color);
      border-radius: var(--radius);
      font-size: 16px;
      resize: none;
      max-height: 200px;
      min-height: 56px;
      background-color: var(--background-primary);
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.05);
    }

    .chat-input:focus {
      outline: none;
      border-color: var(--primary-color);
    }

    .send-button {
      background: none;
      border: none;
      color: var(--primary-color);
      cursor: pointer;
      font-size: 16px;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 36px;
      height: 36px;
      border-radius: 50%;
      transition: all 0.2s;
      padding: 0;
    }

    .send-button:hover {
      background-color: rgba(16, 163, 127, 0.1);
      color: var(--primary-hover);
    }

    footer {
      padding: 15px;
      text-align: center;
      color: var(--text-secondary);
      font-size: 12px;
      border-top: 1px solid var(--border-color);
      background-color: var(--background-primary);
    }

    @media (max-width: 768px) {
      .sidebar {
        display: none;
      }
      
      .suggestions {
        grid-template-columns: 1fr;
      }
      
      .message {
        max-width: 100%;
      }
      
      .header-right {
        flex-direction: column;
        gap: 10px;
        align-items: flex-end;
      }
      
      .header-buttons {
        flex-wrap: wrap;
        justify-content: flex-end;
      }
      
      .history-btn, .quiz-btn-header, .courses-btn-header, .examen-btn-header, .admin-btn, .logout-btn {
        padding: 6px 12px;
        font-size: 12px;
      }
      
      .history-content, .courses-content {
        width: 95%;
        padding: 20px;
      }
      
      .history-actions {
        flex-direction: column;
      }
      
      .chat-input {
        padding-right: 90px;
      }
    }
  </style>

  <script>
    // ===== GESTION DE LA CONNEXION =====
    const loginPage = document.getElementById('loginPage');
    const chatPage = document.getElementById('chatPage');
    const quizPage = document.getElementById('quizPage');
    const examenPage = document.getElementById('examenPage');
    const loginForm = document.getElementById('loginForm');
    const ageInput = document.getElementById('age');
    const ageWarning = document.getElementById('ageWarning');
    const errorMessage = document.getElementById('errorMessage');
    const userDisplay = document.getElementById('userDisplay');
    const userFirstName = document.getElementById('userFirstName');
    const footerUserName = document.getElementById('footerUserName');
    const footerUserAge = document.getElementById('footerUserAge');
    const logoutBtn = document.getElementById('logoutBtn');
    const historyBtn = document.getElementById('historyBtn');
    const startQuizBtn = document.getElementById('startQuizBtn');
    const startExamenBtn = document.getElementById('startExamenBtn');
    const coursesBtn = document.getElementById('coursesBtn');
    const adminBtn = document.getElementById('adminBtn');
    const historyModal = document.getElementById('historyModal');
    const adminModal = document.getElementById('adminModal');
    const coursesModal = document.getElementById('coursesModal');
    const adminContent = document.getElementById('adminContent');
    const coursesContent = document.getElementById('coursesContent');
    const closeHistoryBtn = document.getElementById('closeHistoryBtn');
    const clearHistoryBtn = document.getElementById('clearHistoryBtn');
    const exportHistoryBtn = document.getElementById('exportHistoryBtn');
    const historyList = document.getElementById('historyList');
    const backToChatBtn = document.getElementById('backToChatBtn');
    const backFromExamenBtn = document.getElementById('backFromExamenBtn');
    const quizContent = document.getElementById('quizContent');
    const examenContent = document.getElementById('examenContent');
    const securityIndicator = document.getElementById('securityIndicator');
    const micButton = document.getElementById('micButton');
    const recordingIndicator = document.getElementById('recordingIndicator');
    const stopRecordingBtn = document.getElementById('stopRecording');

    // Variables globales
    let chatHistory = JSON.parse(localStorage.getItem('chellesProjectChatHistory') || '[]');
    let quizResults = JSON.parse(localStorage.getItem('chellesProjectQuizResults') || '[]');
    let examenResults = JSON.parse(localStorage.getItem('chellesProjectExamenResults') || '[]');
    let badges = JSON.parse(localStorage.getItem('chellesProjectBadges') || '{}');
    let currentUser = null;
    let currentQuiz = null;
    let currentExamen = null;
    let userAnswers = [];
    let mediaRecorder = null;
    let audioChunks = [];
    let isRecording = false;

    // ===== MOT DE PASSE ADMIN =====
    const ADMIN_PASSWORD = "azerty";

    // ===== VARIABLES POUR LA SÉCURITÉ DE L'EXAMEN =====
    let examenTimer = null;
    let timeLeft = 20 * 60; // 20 minutes en secondes
    let hasCheated = false;
    let cheatAttempts = 0;
    let lastFocusTime = Date.now();
    let lastVisibilityTime = Date.now();
    let examenStarted = false;

    // ===== BASE DE DONNÉES DES QUESTIONS D'EXAMEN =====
    const EXAMEN_DATABASE = {
      reseaux: [
        {
          question: "Quel protocole est utilisé pour transformer une adresse IP en adresse MAC ?",
          options: ["ARP", "DNS", "DHCP", "ICMP"],
          correct: 0,
          explanation: "ARP (Address Resolution Protocol) transforme les adresses IP en adresses MAC."
        },
        {
          question: "Quelle est la différence entre un switch et un hub ?",
          options: ["Le hub est plus rapide", "Le switch gère les collisions", "Le switch est intelligent et mémorise les adresses MAC", "Le hub a plus de ports"],
          correct: 2,
          explanation: "Un switch est intelligent et mémorise les adresses MAC des appareils connectés."
        },
        {
          question: "Quelle est la plage d'adresses IP privées de classe A ?",
          options: ["10.0.0.0 à 10.255.255.255", "172.16.0.0 à 172.31.255.255", "192.168.0.0 à 192.168.255.255", "169.254.0.0 à 169.254.255.255"],
          correct: 0,
          explanation: "La plage 10.0.0.0 à 10.255.255.255 est réservée pour les adresses privées de classe A."
        },
        {
          question: "Que signifie le terme 'latence' dans un réseau ?",
          options: ["La vitesse de transmission", "Le temps de réponse", "La bande passante", "Le taux d'erreur"],
          correct: 1,
          explanation: "La latence est le temps que met un paquet à voyager de la source à la destination."
        },
        {
          question: "Quel port est utilisé par défaut pour HTTPS ?",
          options: ["80", "443", "22", "21"],
          correct: 1,
          explanation: "Le port 443 est utilisé par défaut pour les connexions HTTPS sécurisées."
        },
        {
          question: "Qu'est-ce qu'une attaque DDoS ?",
          options: ["Vol de données", "Infection par virus", "Saturation d'un service par trop de requêtes", "Interception de communications"],
          correct: 2,
          explanation: "Une attaque DDoS vise à rendre un service indisponible en le submergeant de trafic."
        },
        {
          question: "Quelle est la fonction principale d'un pare-feu ?",
          options: ["Accélérer le réseau", "Filtrer le trafic réseau", "Augmenter la bande passante", "Stocker les données"],
          correct: 1,
          explanation: "Un pare-feu filtre le trafic réseau entrant et sortant selon des règles de sécurité."
        },
        {
          question: "Que signifie VLAN ?",
          options: ["Virtual Local Area Network", "Very Large Area Network", "Variable Local Area Network", "Virtual Linked Area Network"],
          correct: 0,
          explanation: "VLAN permet de créer des réseaux locaux virtuels sur une infrastructure physique."
        },
        {
          question: "Quel est le rôle d'un serveur DHCP ?",
          options: ["Résoudre les noms de domaine", "Attribuer automatiquement des adresses IP", "Sécuriser les connexions", "Héberger des sites web"],
          correct: 1,
          explanation: "DHCP attribue automatiquement des adresses IP aux appareils du réseau."
        },
        {
          question: "Quelle est la différence entre TCP et UDP ?",
          options: ["TCP est plus rapide", "TCP est fiable avec accusé de réception", "UDP est utilisé pour le web", "Aucune différence"],
          correct: 1,
          explanation: "TCP est un protocole fiable avec accusé de réception, UDP est plus rapide mais non fiable."
        }
      ],
      cybersecurite: [
        {
          question: "Qu'est-ce qu'un ransomware ?",
          options: ["Un virus qui vole des mots de passe", "Un logiciel qui chiffre les fichiers contre rançon", "Un spyware", "Un adware"],
          correct: 1,
          explanation: "Un ransomware chiffre les fichiers de la victime et demande une rançon pour les déchiffrer."
        },
        {
          question: "Quelle est la meilleure pratique pour créer un mot de passe fort ?",
          options: ["Utiliser son nom et date de naissance", "Utiliser 12 caractères avec majuscules, minuscules, chiffres et symboles", "Utiliser le même mot de passe partout", "Écrire son mot de passe sur un papier"],
          correct: 1,
          explanation: "Un mot de passe fort doit contenir au moins 12 caractères avec divers types de caractères."
        },
        {
          question: "Qu'est-ce que l'authentification à deux facteurs ?",
          options: ["Deux mots de passe différents", "Un mot de passe et une empreinte digitale", "Deux questions de sécurité", "Un mot de passe et un code temporaire envoyé par SMS"],
          correct: 3,
          explanation: "L'authentification à deux facteurs combine quelque chose que vous connaissez (mot de passe) et quelque chose que vous possédez (code SMS)."
        },
        {
          question: "Qu'est-ce qu'un phishing ?",
          options: ["Une attaque par force brute", "Une tentative d'escroquerie par email", "Un virus informatique", "Une attaque DDoS"],
          correct: 1,
          explanation: "Le phishing consiste à envoyer des emails frauduleux pour voler des informations personnelles."
        },
        {
          question: "Que signifie SSL/TLS ?",
          options: ["Secure Socket Layer / Transport Layer Security", "Simple Security Layer", "System Security Lock", "Server Security Layer"],
          correct: 0,
          explanation: "SSL/TLS sont des protocoles de chiffrement pour sécuriser les communications sur Internet."
        },
        {
          question: "Qu'est-ce qu'un VPN ?",
          options: ["Un virus", "Un réseau privé virtuel", "Un pare-feu", "Un antivirus"],
          correct: 1,
          explanation: "Un VPN crée un tunnel chiffré entre votre appareil et Internet pour protéger votre vie privée."
        },
        {
          question: "Quelle est la différence entre un virus et un ver informatique ?",
          options: ["Le ver se propage seul", "Le virus est plus dangereux", "Le ver ne fait rien", "Aucune différence"],
          correct: 0,
          explanation: "Un ver peut se propager sans intervention humaine, contrairement à un virus qui a besoin d'un programme hôte."
        },
        {
          question: "Qu'est-ce que le chiffrement de bout en bout ?",
          options: ["Chiffrement uniquement côté serveur", "Chiffrement uniquement côté client", "Chiffrement sur tout le trajet", "Pas de chiffrement"],
          correct: 2,
          explanation: "Le chiffrement de bout en bout protège les données tout au long de leur trajet."
        },
        {
          question: "Qu'est-ce qu'un test d'intrusion (pentest) ?",
          options: ["Test de performance", "Simulation d'attaque autorisée", "Test de logiciel", "Audit financier"],
          correct: 1,
          explanation: "Un pentest simule des attaques pour identifier des vulnérabilités de sécurité."
        },
        {
          question: "Que signifie le principe du moindre privilège ?",
          options: ["Donner tous les droits aux utilisateurs", "Donner seulement les droits nécessaires", "Pas de droits aux utilisateurs", "Droits temporaires seulement"],
          correct: 1,
          explanation: "Ce principe accorde aux utilisateurs seulement les permissions nécessaires à leur travail."
        }
      ]
    };

    // ===== BASE DE DONNÉES DES COURS =====
    const COURSES_DATABASE = {
      cloud: {
        title: "Bases du Cloud Computing",
        icon: "☁️",
        color: "#2196F3",
        description: "Introduction aux concepts fondamentaux du cloud computing",
        content: `
          <div class="course-section">
            <h4>🎯 Définition du Cloud Computing</h4>
            <p>Le cloud computing est la fourniture de services informatiques (serveurs, stockage, bases de données, logiciels, analytics, etc.) via Internet ("le cloud").</p>
          </div>
          
          <div class="course-section">
            <h4>📊 Modèles de service cloud</h4>
            <p>Il existe trois principaux modèles de service cloud :</p>
            <ul>
              <li><strong>IaaS (Infrastructure as a Service)</strong> : Fournit une infrastructure informatique virtualisée via Internet (ex: AWS EC2, Azure VMs)</li>
              <li><strong>PaaS (Platform as a Service)</strong> : Fournit une plateforme pour développer, exécuter et gérer des applications (ex: Google App Engine, Heroku)</li>
              <li><strong>SaaS (Software as a Service)</strong> : Fournit des applications logicielles via Internet (ex: Google Workspace, Microsoft 365, Salesforce)</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🌍 Modèles de déploiement</h4>
            <ul>
              <li><strong>Cloud public</strong> : Services offerts par des fournisseurs tiers via Internet public</li>
              <li><strong>Cloud privé</strong> : Infrastructure cloud dédiée à une seule organisation</li>
              <li><strong>Cloud hybride</strong> : Combinaison de cloud public et privé</li>
              <li><strong>Cloud communautaire</strong> : Partagé par plusieurs organisations ayant des préoccupations communes</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>💡 Avantages du cloud</h4>
            <ul>
              <li><strong>Élasticité</strong> : Ajustement automatique des ressources selon la demande</li>
              <li><strong>Flexibilité</strong> : Accès aux ressources depuis n'importe où avec une connexion Internet</li>
              <li><strong>Économique</strong> : Modèle "pay-as-you-go" (payez ce que vous utilisez)</li>
              <li><strong>Haute disponibilité</strong> : Redondance et résilience intégrées</li>
              <li><strong>Mise à l'échelle</strong> : Possibilité de grandir rapidement sans investissement matériel</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🔧 Concepts clés</h4>
            <ul>
              <li><strong>Virtualisation</strong> : Création de ressources informatiques virtuelles</li>
              <li><strong>Conteneurs</strong> : Empaquetage d'applications avec leurs dépendances</li>
              <li><strong>Serverless</strong> : Exécution de code sans gérer l'infrastructure sous-jacente</li>
              <li><strong>Microservices</strong> : Architecture d'applications décomposée en petits services indépendants</li>
              <li><strong>DevOps</strong> : Collaboration entre développement et opérations</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🏢 Principaux fournisseurs</h4>
            <ul>
              <li><strong>Amazon Web Services (AWS)</strong> : Leader du marché avec plus de 200 services</li>
              <li><strong>Microsoft Azure</strong> : Forte intégration avec les produits Microsoft</li>
              <li><strong>Google Cloud Platform (GCP)</strong> : Points forts en IA/ML et data analytics</li>
              <li><strong>IBM Cloud</strong> : Solutions hybrides et AI Watson</li>
              <li><strong>Oracle Cloud</strong> : Spécialisé dans les bases de données</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>📝 Cas d'utilisation courants</h4>
            <ul>
              <li>Hébergement de sites web et d'applications</li>
              <li>Stockage et sauvegarde de données</li>
              <li>Big Data et analytics</li>
              <li>Développement et test d'applications</li>
              <li>Intelligence artificielle et machine learning</li>
              <li>Internet des objets (IoT)</li>
              <li>Streaming de contenu multimédia</li>
            </ul>
          </div>
        `
      },
      reseaux: {
        title: "Bases des Réseaux Informatiques",
        icon: "🌐",
        color: "#4CAF50",
        description: "Fondamentaux des réseaux, protocoles et architecture",
        content: `
          <div class="course-section">
            <h4>🎯 Qu'est-ce qu'un réseau informatique ?</h4>
            <p>Un réseau informatique est un ensemble d'équipements reliés entre eux pour échanger des informations et partager des ressources.</p>
          </div>
          
          <div class="course-section">
            <h4>📡 Types de réseaux</h4>
            <ul>
              <li><strong>PAN (Personal Area Network)</strong> : Réseau personnel (ex: Bluetooth)</li>
              <li><strong>LAN (Local Area Network)</strong> : Réseau local (ex: réseau domestique ou d'entreprise)</li>
              <li><strong>MAN (Metropolitan Area Network)</strong> : Réseau métropolitain</li>
              <li><strong>WAN (Wide Area Network)</strong> : Réseau étendu (ex: Internet)</li>
              <li><strong>WLAN (Wireless LAN)</strong> : Réseau local sans fil (Wi-Fi)</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🔌 Topologies de réseaux</h4>
            <ul>
              <li><strong>Étoile</strong> : Tous les appareils connectés à un concentrateur central</li>
              <li><strong>Bus</strong> : Tous les appareils connectés à un câble principal</li>
              <li><strong>Anneau</strong> : Les appareils forment une boucle fermée</li>
              <li><strong>Maillée</strong> : Chaque appareil est connecté à plusieurs autres</li>
              <li><strong>Arborescente</strong> : Combinaison hiérarchique de plusieurs topologies</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🌐 Modèle OSI (7 couches)</h4>
            <ul>
              <li><strong>Couche 7 : Application</strong> : Interface utilisateur (HTTP, FTP, SMTP)</li>
              <li><strong>Couche 6 : Présentation</strong> : Formatage des données (SSL, JPEG)</li>
              <li><strong>Couche 5 : Session</strong> : Gestion des sessions (RPC, NetBIOS)</li>
              <li><strong>Couche 4 : Transport</strong> : Fiabilité des transmissions (TCP, UDP)</li>
              <li><strong>Couche 3 : Réseau</strong> : Routage et adressage (IP, ICMP)</li>
              <li><strong>Couche 2 : Liaison de données</strong> : Transfert fiable entre nœuds (Ethernet, PPP)</li>
              <li><strong>Couche 1 : Physique</strong> : Support physique (câbles, ondes radio)</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>📨 Protocoles essentiels</h4>
            <ul>
              <li><strong>TCP/IP</strong> : Suite de protocoles pour Internet</li>
              <li><strong>HTTP/HTTPS</strong> : Transfert de pages web</li>
              <li><strong>DNS</strong> : Résolution des noms de domaine en adresses IP</li>
              <li><strong>DHCP</strong> : Attribution automatique d'adresses IP</li>
              <li><strong>FTP/SFTP</strong> : Transfert de fichiers</li>
              <li><strong>SMTP/POP3/IMAP</strong> : Courrier électronique</li>
              <li><strong>SSH</strong> : Connexion sécurisée à distance</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🔐 Adressage IP</h4>
            <p><strong>IPv4</strong> : 32 bits, format décimal (ex: 192.168.1.1)</p>
            <p><strong>IPv6</strong> : 128 bits, format hexadécimal (ex: 2001:0db8:85a3:0000:0000:8a2e:0370:7334)</p>
            <p><strong>Classes d'adresses</strong> : A (1-126), B (128-191), C (192-223), D (224-239 multicast), E (240-255 recherche)</p>
            <p><strong>Adresses privées</strong> : 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16</p>
          </div>
          
          <div class="course-section">
            <h4>🛠️ Équipements réseau</h4>
            <ul>
              <li><strong>Routeur</strong> : Relie différents réseaux et route les paquets</li>
              <li><strong>Switch</strong> : Connecte les appareils dans un même réseau</li>
              <li><strong>Hub</strong> : Concentrateur simple (obsolète)</li>
              <li><strong>Pare-feu</strong> : Filtre le trafic réseau</li>
              <li><strong>Point d'accès</strong> : Permet les connexions sans fil</li>
              <li><strong>Modem</strong> : Convertit les signaux numériques/analogiques</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>📊 Technologies sans fil</h4>
            <ul>
              <li><strong>Wi-Fi (802.11)</strong> : Standards a/b/g/n/ac/ax</li>
              <li><strong>Bluetooth</strong> : Communication courte portée</li>
              <li><strong>4G/5G</strong> : Réseaux cellulaires</li>
              <li><strong>NFC</strong> : Communication champ proche</li>
              <li><strong>LoRaWAN</strong> : Réseaux à faible consommation</li>
            </ul>
          </div>
        `
      },
      cybersecurite: {
        title: "Bases de la Cybersécurité",
        icon: "🛡️",
        color: "#FF5722",
        description: "Protection des systèmes, des réseaux et des données",
        content: `
          <div class="course-section">
            <h4>🎯 Qu'est-ce que la cybersécurité ?</h4>
            <p>La cybersécurité est la pratique qui consiste à protéger les systèmes, les réseaux et les programmes contre les attaques numériques.</p>
          </div>
          
          <div class="course-section">
            <h4>⚠️ Menaces courantes</h4>
            <ul>
              <li><strong>Malware</strong> : Logiciels malveillants (virus, vers, chevaux de Troie)</li>
              <li><strong>Phishing</strong> : Tentative d'escroquerie par email</li>
              <li><strong>Ransomware</strong> : Chiffrement des données contre rançon</li>
              <li><strong>DDoS</strong> : Attaque par déni de service distribué</li>
              <li><strong>Ingénierie sociale</strong> : Manipulation psychologique</li>
              <li><strong>Attaques zero-day</strong> : Exploitation de vulnérabilités inconnues</li>
              <li><strong>MITM</strong> : Attaque de l'homme du milieu</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🔐 Principes fondamentaux</h4>
            <ul>
              <li><strong>Confidentialité</strong> : Seules les personnes autorisées accèdent aux informations</li>
              <li><strong>Intégrité</strong> : Les données ne sont pas modifiées de façon non autorisée</li>
              <li><strong>Disponibilité</strong> : Les systèmes sont accessibles quand nécessaire</li>
              <li><strong>Authentification</strong> : Vérification de l'identité des utilisateurs</li>
              <li><strong>Autorisation</strong> : Définition des droits d'accès</li>
              <li><strong>Non-répudiation</strong> : Impossibilité de nier une action</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🛡️ Mesures de protection</h4>
            <ul>
              <li><strong>Pare-feu</strong> : Filtrage du trafic réseau</li>
              <li><strong>Antivirus/Antimalware</strong> : Détection et suppression des logiciels malveillants</li>
              <li><strong>Chiffrement</strong> : Protection des données sensibles</li>
              <li><strong>VPN</strong> : Tunnel chiffré pour les communications</li>
              <li><strong>Authentification à deux facteurs (2FA)</strong> : Double vérification d'identité</li>
              <li><strong>Sauvegardes régulières</strong> : Protection contre la perte de données</li>
              <li><strong>Mises à jour de sécurité</strong> : Correction des vulnérabilités</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🔍 Types de sécurité</h4>
            <ul>
              <li><strong>Sécurité réseau</strong> : Protection de l'infrastructure réseau</li>
              <li><strong>Sécurité applicative</strong> : Protection des logiciels et applications</li>
              <li><strong>Sécurité des informations</strong> : Protection des données</li>
              <li><strong>Sécurité opérationnelle</strong> : Processus et décisions pour protéger les actifs</li>
              <li><strong>Sécurité physique</strong> : Protection des équipements matériels</li>
              <li><strong>Sécurité du cloud</strong> : Protection des données et applications cloud</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🔒 Bonnes pratiques</h4>
            <ul>
              <li><strong>Mots de passe forts</strong> : Minimum 12 caractères, majuscules, minuscules, chiffres, caractères spéciaux</li>
              <li><strong>Principe du moindre privilège</strong> : Accorder seulement les permissions nécessaires</li>
              <li><strong>Segmentation réseau</strong> : Diviser le réseau en zones de sécurité</li>
              <li><strong>Surveillance continue</strong> : Détection des activités suspectes</li>
              <li><strong>Formation des utilisateurs</strong> : Sensibilisation aux risques</li>
              <li><strong>Plan de réponse aux incidents</strong> : Procédures en cas d'attaque</li>
              <li><strong>Audits réguliers</strong> : Vérification des mesures de sécurité</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>🏛️ Cadres réglementaires</h4>
            <ul>
              <li><strong>RGPD</strong> : Règlement général sur la protection des données (UE)</li>
              <li><strong>ISO 27001</strong> : Norme internationale de sécurité de l'information</li>
              <li><strong>NIST Cybersecurity Framework</strong> : Cadre de cybersécurité (USA)</li>
              <li><strong>ANSSI</strong> : Agence nationale de la sécurité des systèmes d'information (France)</li>
              <li><strong>HIPAA</strong> : Protection des données de santé (USA)</li>
              <li><strong>PCI DSS</strong> : Sécurité des données de cartes de paiement</li>
            </ul>
          </div>
          
          <div class="course-section">
            <h4>📊 Métiers de la cybersécurité</h4>
            <ul>
              <li><strong>Analyste SOC</strong> : Surveillance et réponse aux incidents</li>
              <li><strong>Pentester</strong> : Test d'intrusion éthique</li>
              <li><strong>Architecte sécurité</strong> : Conception des architectures sécurisées</li>
              <li><strong>Consultant en sécurité</strong> : Conseils et audits</li>
              <li><strong>Responsable sécurité</strong> : Management de la sécurité</li>
              <li><strong>Expert forensic</strong> : Investigation numérique</li>
              <li><strong>Spécialiste cryptographie</strong> : Protection par chiffrement</li>
            </ul>
          </div>
        `
      }
    };

    // ===== QUIZ DATABASE - 10 QUESTIONS PAR NIVEAU =====
    const QUIZ_DATABASE = {
      réseaux: {
        beginner: [
          {
            question: "Quel protocole est utilisé pour le streaming vidéo ?",
            options: ["TCP", "UDP", "HTTP", "FTP"],
            correct: 1,
            explanation: "UDP est utilisé pour le streaming car il est plus rapide, même s'il peut perdre des paquets.",
            xp: 10
          },
          {
            question: "Que signifie DNS ?",
            options: ["Digital Network System", "Domain Name System", "Data Network Security", "Dynamic Network Service"],
            correct: 1,
            explanation: "DNS (Domain Name System) traduit les noms de domaine en adresses IP.",
            xp: 10
          },
          {
            question: "Quelle adresse IP est une adresse privée ?",
            options: ["8.8.8.8", "192.168.1.1", "172.217.20.14", "1.1.1.1"],
            correct: 1,
            explanation: "192.168.x.x est une plage d'adresses IP privées réservée aux réseaux locaux.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un routeur ?",
            options: ["Un appareil qui stocke des données", "Un appareil qui dirige le trafic réseau", "Un type de modem", "Un serveur web"],
            correct: 1,
            explanation: "Un routeur dirige les paquets de données entre différents réseaux.",
            xp: 10
          },
          {
            question: "Que signifie LAN ?",
            options: ["Large Area Network", "Local Area Network", "Long Access Network", "Linked Area Network"],
            correct: 1,
            explanation: "LAN signifie Local Area Network (réseau local).",
            xp: 10
          },
          {
            question: "Quelle est la différence entre IPv4 et IPv6 ?",
            options: ["IPv6 est plus sécurisé", "IPv4 a 32 bits, IPv6 a 128 bits", "IPv6 est plus lent", "Aucune différence"],
            correct: 1,
            explanation: "IPv4 utilise des adresses 32 bits, IPv6 utilise des adresses 128 bits.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un pare-feu ?",
            options: ["Un antivirus", "Un système qui filtre le trafic réseau", "Un routeur amélioré", "Un serveur proxy"],
            correct: 1,
            explanation: "Un pare-feu filtre le trafic réseau pour bloquer les connexions non autorisées.",
            xp: 10
          },
          {
            question: "Que signifie WAN ?",
            options: ["Wireless Area Network", "Wide Area Network", "Web Access Network", "Wired Area Network"],
            correct: 1,
            explanation: "WAN signifie Wide Area Network (réseau étendu).",
            xp: 10
          },
          {
            question: "Quel est le rôle d'un switch réseau ?",
            options: ["Connecter des réseaux différents", "Connecter des appareils dans un même réseau", "Convertir des signaux analogiques", "Amplifier le signal WiFi"],
            correct: 1,
            explanation: "Un switch connecte des appareils dans un même réseau local.",
            xp: 10
          },
          {
            question: "Qu'est-ce que le Wi-Fi ?",
            options: ["Un type de câble réseau", "Une technologie de réseau sans fil", "Un protocole de sécurité", "Un fournisseur internet"],
            correct: 1,
            explanation: "Le Wi-Fi est une technologie de réseau local sans fil.",
            xp: 10
          }
        ],
        intermediate: [
          {
            question: "Qu'est-ce que le NAT (Network Address Translation) ?",
            options: ["Un protocole de routage", "Une technique pour traduire les adresses IP", "Un type de firewall", "Un protocole de sécurité"],
            correct: 1,
            explanation: "Le NAT traduit les adresses IP privées en adresses IP publiques.",
            xp: 20
          },
          {
            question: "Quel est le port par défaut pour HTTP ?",
            options: ["80", "443", "21", "25"],
            correct: 0,
            explanation: "Le port 80 est utilisé par défaut pour HTTP.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un subnet mask (masque de sous-réseau) ?",
            options: ["Un filtre de sécurité", "Un identifiant de réseau", "Une adresse MAC", "Un protocole"],
            correct: 1,
            explanation: "Le masque de sous-réseau sépare l'adresse IP en partie réseau et partie hôte.",
            xp: 20
          },
          {
            question: "Que signifie DHCP ?",
            options: ["Dynamic Host Configuration Protocol", "Data Host Communication Protocol", "Digital Host Connection Protocol", "Domain Host Configuration Protocol"],
            correct: 0,
            explanation: "DHCP attribue automatiquement des adresses IP aux appareils.",
            xp: 20
          },
          {
            question: "Quel est le rôle d'un serveur DNS ?",
            options: ["Stocker des pages web", "Traduire les noms de domaine en IP", "Envoyer des emails", "Héberger des fichiers"],
            correct: 1,
            explanation: "Un serveur DNS traduit les noms de domaine en adresses IP.",
            xp: 20
          },
          {
            question: "Qu'est-ce que le modèle OSI ?",
            options: ["Un modèle de réseau physique", "Un modèle de référence à 7 couches", "Un protocole de communication", "Un standard WiFi"],
            correct: 1,
            explanation: "Le modèle OSI divise les communications réseau en 7 couches.",
            xp: 20
          },
          {
            question: "Quelle couche du modèle OSI gère le routage ?",
            options: ["Couche physique", "Couche réseau", "Couche transport", "Couche application"],
            correct: 1,
            explanation: "La couche réseau (layer 3) gère le routage des paquets.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'une adresse MAC ?",
            options: ["Une adresse IP temporaire", "L'adresse physique d'une carte réseau", "Une adresse de serveur", "Un identifiant de domaine"],
            correct: 1,
            explanation: "L'adresse MAC est l'identifiant physique unique d'une carte réseau.",
            xp: 20
          },
          {
            question: "Que signifie VLAN ?",
            options: ["Virtual Local Area Network", "Very Large Area Network", "Variable Local Area Network", "Virtual Linked Area Network"],
            correct: 0,
            explanation: "VLAN permet de segmenter un réseau physique en plusieurs réseaux virtuels.",
            xp: 20
          },
          {
            question: "Quel protocole est utilisé pour les emails ?",
            options: ["FTP", "SMTP", "HTTP", "SSH"],
            correct: 1,
            explanation: "SMTP (Simple Mail Transfer Protocol) est utilisé pour envoyer des emails.",
            xp: 20
          }
        ],
        advanced: [
          {
            question: "Qu'est-ce que BGP (Border Gateway Protocol) ?",
            options: ["Un protocole de messagerie", "Le protocole de routage d'Internet", "Un protocole de sécurité", "Un protocole de transfert de fichiers"],
            correct: 1,
            explanation: "BGP est le protocole utilisé pour router le trafic entre différents systèmes autonomes sur Internet.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'une attaque DDoS ?",
            options: ["Vol de données", "Prise de contrôle d'un serveur", "Saturation d'un service par trop de requêtes", "Infection par virus"],
            correct: 2,
            explanation: "Une attaque DDoS vise à rendre un service indisponible en le submergeant de trafic.",
            xp: 30
          },
          {
            question: "Qu'est-ce que MPLS (Multiprotocol Label Switching) ?",
            options: ["Un protocole de sécurité", "Une technique de routage par étiquettes", "Un type de câblage réseau", "Un standard WiFi"],
            correct: 1,
            explanation: "MPLS utilise des étiquettes pour router les paquets plus efficacement.",
            xp: 30
          },
          {
            question: "Quelle est la différence entre TCP et UDP ?",
            options: ["TCP est plus rapide", "TCP est fiable, UDP ne l'est pas", "UDP est utilisé pour le web", "Aucune différence"],
            correct: 1,
            explanation: "TCP est un protocole fiable avec accusé de réception, UDP est plus rapide mais non fiable.",
            xp: 30
          },
          {
            question: "Qu'est-ce que QoS (Quality of Service) ?",
            options: ["Un système de sécurité", "Une méthode pour prioriser le trafic", "Un type de pare-feu", "Un protocole de routage"],
            correct: 1,
            explanation: "QoS permet de prioriser certains types de trafic sur le réseau.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le spanning tree protocol ?",
            options: ["Un protocole de sécurité", "Un algorithme pour éviter les boucles dans un réseau", "Un protocole de routage", "Une méthode de cryptage"],
            correct: 1,
            explanation: "STP empêche la formation de boucles dans les réseaux avec redondance.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un CDN (Content Delivery Network) ?",
            options: ["Un réseau de serveurs proxy", "Un type de firewall", "Un protocole de streaming", "Un système de stockage"],
            correct: 0,
            explanation: "Un CDN est un réseau de serveurs qui distribue du contenu géographiquement proche des utilisateurs.",
            xp: 30
          },
          {
            question: "Que signifie SD-WAN ?",
            options: ["Software-Defined Wide Area Network", "Secure Data Wide Area Network", "Simple Design Wide Area Network", "Standard Digital Wide Area Network"],
            correct: 0,
            explanation: "SD-WAN utilise des logiciels pour gérer les connexions WAN.",
            xp: 30
          },
          {
            question: "Qu'est-ce que la latence réseau ?",
            options: ["La vitesse de transmission", "Le débit disponible", "Le temps de réponse", "La bande passante"],
            correct: 2,
            explanation: "La latence est le temps que met un paquet pour aller de la source à la destination.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le jitter dans un réseau ?",
            options: ["La variation de la latence", "La perte de paquets", "Le débit maximum", "Le bruit du signal"],
            correct: 0,
            explanation: "Le jitter est la variation du délai entre les paquets successifs.",
            xp: 30
          }
        ]
      },
      cybersécurité: {
        beginner: [
          {
            question: "Qu'est-ce qu'un pare-feu ?",
            options: ["Un antivirus", "Un système qui filtre le trafic réseau", "Un routeur", "Un serveur"],
            correct: 1,
            explanation: "Un pare-feu contrôle et filtre le trafic réseau entrant et sortant.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un VPN ?",
            options: ["Un virus", "Un réseau privé virtuel", "Un pare-feu", "Un antivirus"],
            correct: 1,
            explanation: "Un VPN crée un tunnel chiffré pour sécuriser votre connexion internet.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un virus informatique ?",
            options: ["Un programme utile", "Un programme malveillant", "Un type de firewall", "Un logiciel de sécurité"],
            correct: 1,
            explanation: "Un virus est un programme malveillant qui se réplique et infecte d'autres fichiers.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un mot de passe fort ?",
            options: ["'password'", "'123456'", "'Azerty123!'", "'admin'"],
            correct: 2,
            explanation: "Un mot de passe fort contient majuscules, minuscules, chiffres et caractères spéciaux.",
            xp: 10
          },
          {
            question: "Qu'est-ce que l'authentification à deux facteurs ?",
            options: ["Deux mots de passe", "Un mot de passe et un code SMS", "Deux questions de sécurité", "Un mot de passe et un email"],
            correct: 1,
            explanation: "2FA ajoute une deuxième couche de sécurité après le mot de passe.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un phishing ?",
            options: ["Un type de virus", "Une tentative d'escroquerie par email", "Un attaque DDoS", "Un pare-feu"],
            correct: 1,
            explanation: "Le phishing tente de voler vos informations en se faisant passer pour un tiers de confiance.",
            xp: 10
          },
          {
            question: "Que signifie SSL/TLS ?",
            options: ["Secure Socket Layer / Transport Layer Security", "Simple Security Layer", "System Security Lock", "Server Security Layer"],
            correct: 0,
            explanation: "SSL/TLS chiffre les communications entre un navigateur et un serveur web.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'une mise à jour de sécurité ?",
            options: ["Une nouvelle fonctionnalité", "Un correctif pour des failles", "Un changement d'interface", "Une amélioration de performance"],
            correct: 1,
            explanation: "Les mises à jour de sécurité corrigent des vulnérabilités découvertes.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un ransomware ?",
            options: ["Un virus qui vole des données", "Un logiciel qui chiffre vos fichiers contre rançon", "Un spyware", "Un adware"],
            correct: 1,
            explanation: "Un ransomware chiffre vos fichiers et demande une rançon pour les déchiffrer.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un pare-feu applicatif ?",
            options: ["Un firewall au niveau réseau", "Un firewall qui analyse le trafic applicatif", "Un antivirus", "Un système de détection d'intrusion"],
            correct: 1,
            explanation: "Un pare-feu applicatif analyse le trafic au niveau de la couche application.",
            xp: 10
          }
        ],
        intermediate: [
          {
            question: "Qu'est-ce qu'une attaque par force brute ?",
            options: ["Une attaque physique", "Une tentative de deviner un mot de passe par essais successifs", "Une attaque DDoS", "Un virus"],
            correct: 1,
            explanation: "L'attaque par force brute teste toutes les combinaisons possibles de mots de passe.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un IDS (Intrusion Detection System) ?",
            options: ["Un firewall", "Un système qui détecte les intrusions", "Un antivirus", "Un VPN"],
            correct: 1,
            explanation: "Un IDS surveille le réseau pour détecter des activités suspectes.",
            xp: 20
          },
          {
            question: "Qu'est-ce que le chiffrement de bout en bout ?",
            options: ["Chiffrement uniquement côté serveur", "Chiffrement uniquement côté client", "Chiffrement sur tout le trajet", "Pas de chiffrement"],
            correct: 2,
            explanation: "Le chiffrement de bout en bout protège les données du destinataire à l'expéditeur.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'une attaque XSS (Cross-Site Scripting) ?",
            options: ["Vol de session", "Injection de code dans une page web", "Attaque par déni de service", "Phishing"],
            correct: 1,
            explanation: "XSS injecte du code malveillant dans des pages web consultées par d'autres utilisateurs.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un honeypot ?",
            options: ["Un virus", "Un système leurre pour attirer les hackers", "Un pare-feu", "Un antivirus"],
            correct: 1,
            explanation: "Un honeypot est un système conçu pour attirer et étudier les attaquants.",
            xp: 20
          },
          {
            question: "Qu'est-ce que la segmentation réseau ?",
            options: ["Diviser le réseau en zones de sécurité", "Augmenter la vitesse du réseau", "Ajouter des routeurs", "Installer des firewalls"],
            correct: 0,
            explanation: "La segmentation limite la propagation des attaques en divisant le réseau.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'une attaque MITM (Man-in-the-Middle) ?",
            options: ["Attaque par déni de service", "Interception des communications", "Vol de mot de passe par force brute", "Infection par virus"],
            correct: 1,
            explanation: "Une attaque MITM intercepte et modifie les communications entre deux parties.",
            xp: 20
          },
          {
            question: "Que signifie SOC (Security Operations Center) ?",
            options: ["System Operations Center", "Security Operations Center", "Server Operations Center", "Software Operations Center"],
            correct: 1,
            explanation: "Un SOC est une équipe qui surveille et répond aux incidents de sécurité.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un token de sécurité ?",
            options: ["Un mot de passe", "Un dispositif physique pour l'authentification", "Un certificat SSL", "Une clé de chiffrement"],
            correct: 1,
            explanation: "Un token génère des codes à usage unique pour l'authentification.",
            xp: 20
          },
          {
            question: "Qu'est-ce que le principe du moindre privilège ?",
            options: ["Donner tous les droits aux utilisateurs", "Donner seulement les droits nécessaires", "Pas de droits aux utilisateurs", "Droits temporaires seulement"],
            correct: 1,
            explanation: "Ce principe accorde aux utilisateurs seulement les permissions nécessaires à leur travail.",
            xp: 20
          }
        ],
        advanced: [
          {
            question: "Qu'est-ce qu'une attaque par ingénierie sociale avancée ?",
            options: ["Attaque technique pure", "Manipulation psychologique sophistiquée", "Attaque par force brute", "Exploitation de failles logicielles"],
            correct: 1,
            explanation: "L'ingénierie sociale avancée utilise des techniques psychologiques complexes pour tromper.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un APT (Advanced Persistent Threat) ?",
            options: ["Un virus simple", "Une attaque persistante et sophistiquée", "Une attaque DDoS", "Un phishing basique"],
            correct: 1,
            explanation: "Un APT est une attaque longue et sophistiquée souvent menée par des états-nations.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le modèle de sécurité Zero Trust ?",
            options: ["Faire confiance à tout le monde à l'intérieur", "Ne faire confiance à personne, même à l'intérieur", "Faire confiance seulement aux administrateurs", "Pas de sécurité"],
            correct: 1,
            explanation: "Zero Trust suppose que toute personne ou dispositif peut être compromis.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'une attaque par chaîne d'approvisionnement ?",
            options: ["Attaquer directement la cible", "Attaquer via un fournisseur de la cible", "Attaque par email", "Attaque physique"],
            correct: 1,
            explanation: "Cette attaque compromet un fournisseur pour atteindre sa cible finale.",
            xp: 30
          },
          {
            question: "Qu'est-ce que la cryptographie post-quantique ?",
            options: ["Cryptographie pour les quantités", "Cryptographie résistante aux ordinateurs quantiques", "Cryptographie quantique", "Cryptographie ancienne"],
            correct: 1,
            explanation: "Algorithmes cryptographiques conçus pour résister aux attaques des ordinateurs quantiques.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un SIEM (Security Information and Event Management) ?",
            options: ["Un firewall", "Un système de collecte et d'analyse des logs de sécurité", "Un antivirus", "Un IDS"],
            correct: 1,
            explanation: "Un SIEM collecte et analyse les événements de sécurité de diverses sources.",
            xp: 30
          },
          {
            question: "Qu'est-ce que la gestion des identités et des accès (IAM) ?",
            options: ["Gestion des firewalls", "Gestion des utilisateurs et leurs permissions", "Gestion des serveurs", "Gestion des réseaux"],
            correct: 1,
            explanation: "IAM gère les identités numériques et contrôle leur accès aux ressources.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un test d'intrusion (pentest) ?",
            options: ["Test de performance", "Simulation d'attaque autorisée", "Test de logiciel", "Audit financier"],
            correct: 1,
            explanation: "Un pentest simule des attaques pour identifier des vulnérabilités.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le bug bounty ?",
            options: ["Un virus", "Un programme qui récompense les chercheurs qui trouvent des bugs", "Un type de firewall", "Un protocole de sécurité"],
            correct: 1,
            explanation: "Un programme qui rémunère les chercheurs pour la découverte de vulnérabilités.",
            xp: 30
          },
          {
            question: "Qu'est-ce que la résilience cyber ?",
            options: ["La capacité à prévenir toutes les attaques", "La capacité à résister et récupérer après une attaque", "La vitesse de réponse", "Le nombre de firewalls"],
            correct: 1,
            explanation: "La capacité d'un système à continuer de fonctionner malgré une cyberattaque.",
            xp: 30
          }
        ]
      },
      cloud: {
        beginner: [
          {
            question: "Qu'est-ce que le cloud computing ?",
            options: ["Des ordinateurs dans les nuages", "L'utilisation de services informatiques à distance", "Un type de réseau sans fil", "Un système d'exploitation"],
            correct: 1,
            explanation: "Le cloud computing permet d'utiliser des ressources informatiques via Internet.",
            xp: 10
          },
          {
            question: "Quels sont les trois principaux modèles de service cloud ?",
            options: ["IaaS, PaaS, SaaS", "HTTP, FTP, SMTP", "LAN, WAN, MAN", "TCP, UDP, IP"],
            correct: 0,
            explanation: "IaaS (Infrastructure), PaaS (Platform), SaaS (Software) as a Service.",
            xp: 10
          },
          {
            question: "Qu'est-ce que SaaS ?",
            options: ["Storage as a Service", "Software as a Service", "Security as a Service", "System as a Service"],
            correct: 1,
            explanation: "SaaS fournit des applications logicielles via Internet.",
            xp: 10
          },
          {
            question: "Quel est le principal avantage du cloud ?",
            options: ["Coût fixe", "Flexibilité et élasticité", "Vitesse garantie", "Sécurité absolue"],
            correct: 1,
            explanation: "Le cloud permet de monter ou descendre en puissance selon les besoins.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'un data center ?",
            options: ["Un centre commercial", "Un bâtiment qui héberge des serveurs", "Un centre de données météo", "Un centre de recherche"],
            correct: 1,
            explanation: "Un data center est une installation qui héberge des équipements informatiques.",
            xp: 10
          },
          {
            question: "Que signifie 'élasticité' dans le cloud ?",
            options: ["Flexibilité des prix", "Capacité à s'adapter aux besoins", "Résistance physique", "Compatibilité"],
            correct: 1,
            explanation: "L'élasticité permet d'ajuster automatiquement les ressources à la demande.",
            xp: 10
          },
          {
            question: "Qu'est-ce que le modèle 'pay-as-you-go' ?",
            options: ["Paiement mensuel fixe", "Paiement à l'utilisation", "Gratuité totale", "Paiement annuel"],
            correct: 1,
            explanation: "Vous payez seulement pour les ressources que vous utilisez réellement.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'une région cloud ?",
            options: ["Un pays", "Une zone géographique avec des data centers", "Un type de service", "Un protocole"],
            correct: 1,
            explanation: "Une région est une zone géographique où un fournisseur cloud a des data centers.",
            xp: 10
          },
          {
            question: "Qu'est-ce qu'une instance cloud ?",
            options: ["Un serveur virtuel", "Une application", "Une base de données", "Un réseau"],
            correct: 0,
            explanation: "Une instance est un serveur virtuel dans le cloud.",
            xp: 10
          },
          {
            question: "Que signifie 'multi-locataire' dans le cloud ?",
            options: ["Plusieurs propriétaires", "Partage de ressources entre clients", "Plusieurs data centers", "Plusieurs services"],
            correct: 1,
            explanation: "L'architecture multi-locataire permet à plusieurs clients de partager les mêmes ressources.",
            xp: 10
          }
        ],
        intermediate: [
          {
            question: "Quelle est la différence entre scalabilité verticale et horizontale ?",
            options: ["Verticale: ajouter des serveurs, Horizontale: améliorer un serveur", "Verticale: améliorer un serveur, Horizontale: ajouter des serveurs", "Pas de différence", "Verticale pour stockage, Horizontale pour calcul"],
            correct: 1,
            explanation: "Scalabilité verticale = plus de puissance à un serveur, horizontale = plus de serveurs.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un VPC (Virtual Private Cloud) ?",
            options: ["Un cloud public", "Un réseau virtuel isolé dans le cloud", "Un type de VPN", "Un serveur privé"],
            correct: 1,
            explanation: "Un VPC est un réseau virtuel isolé dédié à votre compte cloud.",
            xp: 20
          },
          {
            question: "Qu'est-ce que la haute disponibilité (HA) ?",
            options: ["Vitesse élevée", "Capacité à rester opérationnel", "Grande capacité de stockage", "Faible latence"],
            correct: 1,
            explanation: "La HA minimise les temps d'arrêt grâce à la redondance.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un load balancer ?",
            options: ["Un firewall", "Un distributeur de charge", "Un routeur", "Un serveur web"],
            correct: 1,
            explanation: "Un load balancer répartit le trafic entre plusieurs serveurs.",
            xp: 20
          },
          {
            question: "Que signifie 'serverless' ?",
            options: ["Sans serveur physique", "Sans code", "Sans réseau", "Sans stockage"],
            correct: 0,
            explanation: "Serverless permet d'exécuter du code sans gérer les serveurs sous-jacents.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'un container ?",
            options: ["Un serveur virtuel", "Un paquet logiciel isolé", "Une base de données", "Un réseau"],
            correct: 1,
            explanation: "Un container empaquette une application avec ses dépendances.",
            xp: 20
          },
          {
            question: "Qu'est-ce que Docker ?",
            options: ["Un système d'exploitation", "Une plateforme de conteneurisation", "Un langage de programmation", "Un fournisseur cloud"],
            correct: 1,
            explanation: "Docker est une plateforme pour créer, déployer et gérer des conteneurs.",
            xp: 20
          },
          {
            question: "Qu'est-ce que Kubernetes ?",
            options: ["Un système de stockage", "Un orchestrateur de conteneurs", "Un langage de script", "Un service de base de données"],
            correct: 1,
            explanation: "Kubernetes automatise le déploiement et la gestion des conteneurs.",
            xp: 20
          },
          {
            question: "Qu'est-ce qu'une zone de disponibilité ?",
            options: ["Un pays", "Un data center isolé dans une région", "Un continent", "Un bâtiment"],
            correct: 1,
            explanation: "Une zone de disponibilité est un data center isolé avec son propre alimentation et réseau.",
            xp: 20
          },
          {
            question: "Qu'est-ce que l'infrastructure as code (IaC) ?",
            options: ["Coder des applications", "Gérer l'infrastructure via du code", "Coder des bases de données", "Programmer des réseaux"],
            correct: 1,
            explanation: "IaC permet de provisionner et gérer l'infrastructure via des fichiers de configuration.",
            xp: 20
          }
        ],
        advanced: [
          {
            question: "Qu'est-ce qu'un cloud hybride ?",
            options: ["Cloud public seulement", "Cloud privé seulement", "Combinaison de cloud public et privé", "Cloud communautaire"],
            correct: 2,
            explanation: "Un cloud hybride combine cloud public et infrastructure privée on-premise.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le cloud natif (cloud-native) ?",
            options: ["Applications conçues pour le cloud", "Applications migrées vers le cloud", "Applications hors cloud", "Applications web simples"],
            correct: 0,
            explanation: "Les applications cloud-native sont conçues dès le départ pour le cloud.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un service mesh ?",
            options: ["Un réseau physique", "Une couche d'abstraction pour la communication entre services", "Un firewall", "Un load balancer"],
            correct: 1,
            explanation: "Un service mesh gère la communication entre les microservices.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le FinOps ?",
            options: ["Gestion financière du cloud", "Opérations réseau", "Sécurité cloud", "Développement cloud"],
            correct: 0,
            explanation: "FinOps optimise les coûts cloud grâce à la collaboration entre finance, IT et devs.",
            xp: 30
          },
          {
            question: "Qu'est-ce que l'observabilité dans le cloud ?",
            options: ["Surveillance basique", "Mesures, logs et traces pour comprendre le système", "Audit de sécurité", "Gestion des utilisateurs"],
            correct: 1,
            explanation: "L'observabilité permet de comprendre l'état interne d'un système via ses sorties.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un cloud souverain ?",
            options: ["Cloud public international", "Cloud conforme aux régulations d'un pays", "Cloud privé d'entreprise", "Cloud gratuit"],
            correct: 1,
            explanation: "Un cloud souverain répond aux exigences légales et de souveraineté d'un pays.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le edge computing ?",
            options: ["Calcul centralisé", "Calcul à la périphérie du réseau, près des utilisateurs", "Calcul quantique", "Calcul distribué"],
            correct: 1,
            explanation: "Le edge computing traite les données près de leur source pour réduire la latence.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'une architecture event-driven ?",
            options: ["Architecture basée sur des requêtes", "Architecture basée sur des événements", "Architecture monolithique", "Architecture client-serveur"],
            correct: 1,
            explanation: "Une architecture event-driven réagit à des événements plutôt qu'à des requêtes.",
            xp: 30
          },
          {
            question: "Qu'est-ce que le serverless computing ?",
            options: ["Exécution de code sans provisionner de serveurs", "Serveurs physiques uniquement", "Virtualisation complète", "Conteneurs seulement"],
            correct: 0,
            explanation: "Serverless exécute du code en réponse à des événements sans gestion de serveur.",
            xp: 30
          },
          {
            question: "Qu'est-ce qu'un cloud broker ?",
            options: ["Un fournisseur cloud", "Un intermédiaire qui gère plusieurs clouds", "Un client cloud", "Un développeur cloud"],
            correct: 1,
            explanation: "Un cloud broker aide les entreprises à gérer et intégrer plusieurs services cloud.",
            xp: 30
          }
        ]
      }
    };

    // ===== INITIALISATION =====
    window.addEventListener('DOMContentLoaded', () => {
      const savedUser = localStorage.getItem('chellesProjectUser');
      if (savedUser) {
        const user = JSON.parse(savedUser);
        if (user.age > 14) {
          currentUser = user;
          loginUser(user);
        }
      }
    });

    // ===== CONNEXION UTILISATEUR =====
    ageInput.addEventListener('input', function() {
      const age = parseInt(this.value);
      if (age && age <= 14) {
        ageWarning.style.display = 'block';
      } else {
        ageWarning.style.display = 'none';
      }
    });

    loginForm.addEventListener('submit', function(e) {
      e.preventDefault();
      
      const firstName = document.getElementById('firstName').value.trim();
      const lastName = document.getElementById('lastName').value.trim();
      const age = parseInt(ageInput.value);
      
      if (!firstName || !lastName || !age || age <= 0) {
        showError("Veuillez remplir tous les champs correctement.");
        return;
      }
      
      if (age <= 14) {
        showError("Vous devez avoir plus de 14 ans pour accéder au chatbot.");
        return;
      }
      
      const user = {
        firstName: firstName,
        lastName: lastName,
        age: age,
        loginTime: new Date().toISOString()
      };
      
      localStorage.setItem('chellesProjectUser', JSON.stringify(user));
      currentUser = user;
      loginUser(user);
    });

    function showError(message) {
      errorMessage.textContent = message;
      errorMessage.style.display = 'block';
      setTimeout(() => {
        errorMessage.style.display = 'none';
      }, 5000);
    }

    function loginUser(user) {
      userDisplay.textContent = `${user.firstName} ${user.lastName}`;
      userFirstName.textContent = user.firstName;
      footerUserName.textContent = `${user.firstName} ${user.lastName}`;
      footerUserAge.textContent = user.age;
      
      loginPage.style.display = 'none';
      chatPage.style.display = 'flex';
      
      const welcomeMessage = document.querySelector('.message-content');
      if (welcomeMessage) {
        welcomeMessage.innerHTML = `👋 Salut <strong>${user.firstName}</strong> ! Je suis <strong>Chelles Project</strong>, ton assistant d'informatique. Pose-moi une question sur les réseaux, le matériel, la sécurité ou la programmation.`;
      }
    }

    // ===== DÉCONNEXION =====
    logoutBtn.addEventListener('click', function() {
      if (confirm("Voulez-vous vous déconnecter ?")) {
        localStorage.removeItem('chellesProjectUser');
        currentUser = null;
        document.getElementById('loginForm').reset();
        chatPage.style.display = 'none';
        quizPage.style.display = 'none';
        examenPage.style.display = 'none';
        loginPage.style.display = 'flex';
      }
    });

    // ===== SYSTÈME D'EXAMEN =====
    startExamenBtn.addEventListener('click', function() {
      showExamenInstructions();
    });

    backFromExamenBtn.addEventListener('click', function() {
      if (examenStarted) {
        if (confirm("Êtes-vous sûr de vouloir quitter l'examen ? Votre progression sera perdue.")) {
          stopExamen();
          examenPage.style.display = 'none';
          chatPage.style.display = 'flex';
        }
      } else {
        examenPage.style.display = 'none';
        chatPage.style.display = 'flex';
      }
    });

    function showExamenInstructions() {
      examenContent.innerHTML = `
        <div class="examen-header">
          <h2>📋 Examen Certifiant Chelles Project</h2>
          <p>Testez vos connaissances pour obtenir le badge "Expert Chelles Project"</p>
        </div>
        
        <div class="examen-question">
          <h3>Instructions importantes :</h3>
          <ul style="margin: 20px 0; padding-left: 20px; color: var(--text-secondary);">
            <li>⏱️ <strong>Durée : 20 minutes</strong> - Le chronomètre démarre dès que vous commencez</li>
            <li>📝 <strong>30 questions</strong> - 15 réseaux + 15 cybersécurité</li>
            <li>🎯 <strong>Seuil de réussite : 60%</strong> - Minimum 18/30 bonnes réponses</li>
            <li>🛡️ <strong>Sécurité active</strong> - La triche sera détectée et signalée</li>
            <li>🏆 <strong>Badge à gagner</strong> - "Expert Chelles Project"</li>
          </ul>
          
          <div style="background: rgba(243, 156, 18, 0.1); padding: 15px; border-radius: var(--radius); border-left: 4px solid var(--examen-color); margin: 20px 0;">
            <h4>⚠️ Règles de sécurité :</h4>
            <ul style="margin: 10px 0; padding-left: 20px;">
              <li>Ne pas changer d'onglet pendant l'examen</li>
              <li>Ne pas minimiser la fenêtre</li>
              <li>Ne pas utiliser d'autres applications</li>
              <li>Une alerte sera déclenchée en cas de triche</li>
              <li>3 alertes = Échec automatique</li>
            </ul>
          </div>
          
          <div style="text-align: center; margin-top: 30px;">
            <button class="examen-btn" onclick="startExamen()" style="padding: 15px 40px; font-size: 18px;">
              🚀 Commencer l'Examen
            </button>
            <button class="examen-btn secondary" onclick="backFromExamenBtn.click()" style="margin-left: 15px;">
              ← Retour
            </button>
          </div>
        </div>
      `;
      
      chatPage.style.display = 'none';
      examenPage.style.display = 'flex';
    }

    function startExamen() {
      examenStarted = true;
      timeLeft = 20 * 60; // 20 minutes
      hasCheated = false;
      cheatAttempts = 0;
      
      // Créer les questions mélangées
      const reseauxQuestions = [...EXAMEN_DATABASE.reseaux];
      const cybersecuriteQuestions = [...EXAMEN_DATABASE.cybersecurite];
      
      // Mélanger les questions
      const shuffleArray = (array) => {
        for (let i = array.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [array[i], array[j]] = [array[j], array[i]];
        }
        return array;
      };
      
      shuffleArray(reseauxQuestions);
      shuffleArray(cybersecuriteQuestions);
      
      // Prendre 15 questions de chaque catégorie
      const selectedReseaux = reseauxQuestions.slice(0, 15);
      const selectedCybersecurite = cybersecuriteQuestions.slice(0, 15);
      
      // Combiner et mélanger toutes les questions
      const allQuestions = [...selectedReseaux, ...selectedCybersecurite];
      shuffleArray(allQuestions);
      
      currentExamen = {
        questions: allQuestions,
        currentQuestion: 0,
        answers: [],
        startTime: new Date().toISOString(),
        cheatDetected: false
      };
      
      userAnswers = new Array(allQuestions.length).fill(null);
      
      // Démarrer le chronomètre
      startTimer();
      
      // Activer la surveillance de sécurité
      setupSecurityMonitoring();
      
      showExamenQuestion();
    }

    function startTimer() {
      updateTimerDisplay();
      
      examenTimer = setInterval(() => {
        timeLeft--;
        updateTimerDisplay();
        
        if (timeLeft <= 0) {
          clearInterval(examenTimer);
          timeUp();
        }
      }, 1000);
    }

    function updateTimerDisplay() {
      const minutes = Math.floor(timeLeft / 60);
      const seconds = timeLeft % 60;
      const timerDisplay = document.createElement('div');
      timerDisplay.className = `examen-timer ${timeLeft < 300 ? 'timer-warning' : ''}`;
      timerDisplay.id = 'examenTimerDisplay';
      timerDisplay.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
      
      const existingTimer = document.getElementById('examenTimerDisplay');
      if (existingTimer) {
        existingTimer.replaceWith(timerDisplay);
      } else {
        document.body.appendChild(timerDisplay);
      }
    }

    function setupSecurityMonitoring() {
      // Surveiller le changement d'onglet
      document.addEventListener('visibilitychange', () => {
        if (document.hidden && examenStarted) {
          detectCheating("Changement d'onglet détecté");
        }
        lastVisibilityTime = Date.now();
      });
      
      // Surveiller le focus de la fenêtre
      window.addEventListener('blur', () => {
        if (examenStarted) {
          detectCheating("Fenêtre perdue du focus");
        }
        lastFocusTime = Date.now();
      });
      
      // Surveiller les raccourcis clavier
      document.addEventListener('keydown', (e) => {
        if (examenStarted && (e.ctrlKey || e.metaKey)) {
          if (e.key === 'c' || e.key === 'v' || e.key === 't' || e.key === 'n') {
            e.preventDefault();
            detectCheating("Raccourci clavier interdit détecté");
          }
        }
        
        // Bloquer F5 et F12
        if (e.key === 'F5' || e.key === 'F12') {
          e.preventDefault();
          detectCheating("Touche de fonction bloquée");
        }
      });
      
      // Empêcher le clic droit
      document.addEventListener('contextmenu', (e) => {
        if (examenStarted) {
          e.preventDefault();
          detectCheating("Clic droit bloqué");
        }
      });
    }

    function detectCheating(reason) {
      if (!examenStarted || hasCheated) return;
      
      cheatAttempts++;
      
      if (cheatAttempts >= 3) {
        hasCheated = true;
        currentExamen.cheatDetected = true;
        
        // Afficher l'alerte
        showCheatingWarning("⚠️ TRICHE DÉTECTÉE ! L'examen est automatiquement échoué.");
        
        // Arrêter l'examen après 3 secondes
        setTimeout(() => {
          finishExamen(false);
        }, 3000);
      } else {
        showCheatingWarning(`⚠️ Attention ! ${reason} (Tentative ${cheatAttempts}/3)`);
      }
      
      // Mettre à jour l'indicateur de sécurité
      securityIndicator.className = 'security-indicator warning';
      securityIndicator.innerHTML = '<span>⚠️</span> <span>Sécurité compromise</span>';
    }

    function showCheatingWarning(message) {
      const warning = document.createElement('div');
      warning.className = 'cheating-warning';
      warning.textContent = message;
      
      // Supprimer les avertissements précédents
      const existingWarnings = document.querySelectorAll('.cheating-warning');
      existingWarnings.forEach(w => w.remove());
      
      document.body.appendChild(warning);
      
      // Supprimer après 5 secondes
      setTimeout(() => {
        warning.remove();
      }, 5000);
    }

    function showExamenQuestion() {
      if (!currentExamen || currentExamen.currentQuestion >= currentExamen.questions.length) {
        finishExamen(true);
        return;
      }
      
      const question = currentExamen.questions[currentExamen.currentQuestion];
      const progress = ((currentExamen.currentQuestion + 1) / currentExamen.questions.length) * 100;
      
      examenContent.innerHTML = `
        <div class="examen-header">
          <h2>Examen en cours</h2>
          <p>Question ${currentExamen.currentQuestion + 1} / ${currentExamen.questions.length}</p>
        </div>
        
        <div class="examen-progress">
          <div>Progression</div>
          <div class="progress-bar">
            <div class="progress-fill" style="width: ${progress}%"></div>
          </div>
        </div>
        
        <div class="examen-question">
          <div class="examen-question-number">
            ${currentExamen.currentQuestion < 15 ? '📡 Réseaux' : '🛡️ Cybersécurité'}
          </div>
          <h3 style="margin-bottom: 20px;">${question.question}</h3>
          <div class="examen-options">
            ${question.options.map((option, index) => `
              <button class="examen-option ${userAnswers[currentExamen.currentQuestion] === index ? 'selected' : ''}" 
                      data-index="${index}"
                      onclick="selectExamenAnswer(${index})">
                ${option}
              </button>
            `).join('')}
          </div>
        </div>
        
        <div class="examen-navigation">
          <button class="examen-btn secondary" onclick="previousExamenQuestion()" ${currentExamen.currentQuestion === 0 ? 'disabled' : ''}>
            ← Précédent
          </button>
          
          ${currentExamen.currentQuestion < currentExamen.questions.length - 1 ? `
            <button class="examen-btn" onclick="nextExamenQuestion()" ${userAnswers[currentExamen.currentQuestion] === null ? 'disabled' : ''}>
              Suivant →
            </button>
          ` : `
            <button class="examen-btn" onclick="finishExamen(true)" ${userAnswers[currentExamen.currentQuestion] === null ? 'disabled' : ''}>
              🏁 Terminer l'examen
            </button>
          `}
        </div>
      `;
    }

    function selectExamenAnswer(index) {
      userAnswers[currentExamen.currentQuestion] = index;
      showExamenQuestion();
    }

    function previousExamenQuestion() {
      if (currentExamen.currentQuestion > 0) {
        currentExamen.currentQuestion--;
        showExamenQuestion();
      }
    }

    function nextExamenQuestion() {
      if (currentExamen.currentQuestion < currentExamen.questions.length - 1 && userAnswers[currentExamen.currentQuestion] !== null) {
        currentExamen.currentQuestion++;
        showExamenQuestion();
      }
    }

    function timeUp() {
      showCheatingWarning("⏰ Temps écoulé ! L'examen se termine automatiquement.");
      setTimeout(() => {
        finishExamen(true);
      }, 2000);
    }

    function finishExamen(normalFinish) {
      if (examenTimer) {
        clearInterval(examenTimer);
      }
      
      // Supprimer le timer
      const timerDisplay = document.getElementById('examenTimerDisplay');
      if (timerDisplay) {
        timerDisplay.remove();
      }
      
      // Calculer le score
      let score = 0;
      currentExamen.questions.forEach((question, index) => {
        if (userAnswers[index] === question.correct) {
          score++;
        }
      });
      
      const percentage = Math.round((score / currentExamen.questions.length) * 100);
      const passed = percentage >= 60 && !hasCheated && normalFinish;
      
      // Enregistrer le résultat
      saveExamenResult(score, percentage, passed);
      
      // Afficher les résultats
      showExamenResults(score, percentage, passed);
      
      examenStarted = false;
    }

    function showExamenResults(score, percentage, passed) {
      const badgeEarned = passed && percentage >= 60;
      
      examenContent.innerHTML = `
        <div class="examen-results">
          <h2>${passed ? '🎉 FÉLICITATIONS !' : hasCheated ? '❌ ÉCHEC - TRICHE DÉTECTÉE' : '📝 Résultats de l\'Examen'}</h2>
          
          ${badgeEarned ? `
            <div class="badge-earned">
              <div class="badge-icon">🏆</div>
              <div>Expert</div>
              <div>Chelles Project</div>
            </div>
          ` : `
            <div class="score-circle" style="background: ${passed ? 'var(--success-color)' : 'var(--warning-color)'}; margin-bottom: 30px;">
              <span style="font-size: 32px;">${score}/${currentExamen.questions.length}</span>
              <span style="font-size: 16px;">${percentage}%</span>
            </div>
          `}
          
          <p class="score-text">
            ${hasCheated ? '❌ Vous avez été détecté en train de tricher. Le badge n\'est pas accordé.' :
              passed ? `✅ Vous avez réussi l'examen avec ${percentage}% de bonnes réponses !` :
              `📚 Vous avez obtenu ${percentage}%. Il faut 60% pour obtenir le badge. Continuez à vous entraîner !`}
          </p>
          
          ${badgeEarned ? `
            <div style="background: rgba(46, 204, 113, 0.1); padding: 20px; border-radius: var(--radius); margin: 20px auto; max-width: 500px;">
              <h3>🏆 Badge débloqué : Expert Chelles Project</h3>
              <p>Félicitations ! Vous avez démontré une excellente maîtrise des concepts réseaux et cybersécurité.</p>
              <p>Ce badge est enregistré dans votre profil et peut être partagé.</p>
            </div>
          ` : ''}
          
          <div style="margin-top: 40px;">
            <button class="examen-btn" onclick="backFromExamenBtn.click()" style="margin-right: 10px;">
              ← Retour au Chat
            </button>
            ${!passed && !hasCheated ? `
              <button class="examen-btn secondary" onclick="showExamenInstructions()">
                🔄 Réessayer
              </button>
            ` : ''}
          </div>
        </div>
      `;
    }

    function saveExamenResult(score, percentage, passed) {
      if (!currentUser) return;
      
      const result = {
        userId: `${currentUser.firstName} ${currentUser.lastName}`,
        score: score,
        total: currentExamen.questions.length,
        percentage: percentage,
        passed: passed,
        cheatDetected: hasCheated,
        timeSpent: (20 * 60) - timeLeft,
        date: new Date().toISOString()
      };
      
      examenResults.push(result);
      localStorage.setItem('chellesProjectExamenResults', JSON.stringify(examenResults));
      
      // Si réussi, attribuer le badge
      if (passed) {
        if (!badges[currentUser.firstName + currentUser.lastName]) {
          badges[currentUser.firstName + currentUser.lastName] = [];
        }
        
        if (!badges[currentUser.firstName + currentUser.lastName].includes('expert')) {
          badges[currentUser.firstName + currentUser.lastName].push('expert');
          localStorage.setItem('chellesProjectBadges', JSON.stringify(badges));
        }
      }
    }

    function stopExamen() {
      if (examenTimer) {
        clearInterval(examenTimer);
      }
      
      const timerDisplay = document.getElementById('examenTimerDisplay');
      if (timerDisplay) {
        timerDisplay.remove();
      }
      
      examenStarted = false;
      hasCheated = false;
      currentExamen = null;
    }

    // ===== QUIZ SYSTEM =====
    startQuizBtn.addEventListener('click', function() {
      showQuizSelection();
    });

    backToChatBtn.addEventListener('click', function() {
      quizPage.style.display = 'none';
      chatPage.style.display = 'flex';
    });

    function showQuizSelection() {
      quizContent.innerHTML = `
        <div class="quiz-selection-container">
          <div class="quiz-header">
            <h2>📝 Choisissez Votre Quiz</h2>
            <p>Sélectionnez une catégorie et un niveau de difficulté (10 questions par quiz)</p>
          </div>
          
          <div class="quiz-category">
            <div class="category-header">
              <div class="category-icon" style="background: #2196f3;">🌐</div>
              <div>
                <div class="category-title">Réseaux Informatiques</div>
                <div class="category-description">Apprenez les bases des réseaux, protocoles et infrastructure</div>
              </div>
            </div>
            <div class="difficulty-levels">
              <button class="difficulty-btn beginner" onclick="startSpecificQuiz('réseaux', 'beginner')">
                <div class="difficulty-name">Débutant</div>
                <div class="difficulty-xp">10 XP par question</div>
              </button>
              <button class="difficulty-btn intermediate" onclick="startSpecificQuiz('réseaux', 'intermediate')">
                <div class="difficulty-name">Moyen</div>
                <div class="difficulty-xp">20 XP par question</div>
              </button>
              <button class="difficulty-btn advanced" onclick="startSpecificQuiz('réseaux', 'advanced')">
                <div class="difficulty-name">Difficile</div>
                <div class="difficulty-xp">30 XP par question</div>
              </button>
            </div>
          </div>
          
          <div class="quiz-category">
            <div class="category-header">
              <div class="category-icon" style="background: #4caf50;">🛡️</div>
              <div>
                <div class="category-title">Cybersécurité</div>
                <div class="category-description">Protégez vos données et comprenez les menaces en ligne</div>
              </div>
            </div>
            <div class="difficulty-levels">
              <button class="difficulty-btn beginner" onclick="startSpecificQuiz('cybersécurité', 'beginner')">
                <div class="difficulty-name">Débutant</div>
                <div class="difficulty-xp">10 XP par question</div>
              </button>
              <button class="difficulty-btn intermediate" onclick="startSpecificQuiz('cybersécurité', 'intermediate')">
                <div class="difficulty-name">Moyen</div>
                <div class="difficulty-xp">20 XP par question</div>
              </button>
              <button class="difficulty-btn advanced" onclick="startSpecificQuiz('cybersécurité', 'advanced')">
                <div class="difficulty-name">Difficile</div>
                <div class="difficulty-xp">30 XP par question</div>
              </button>
            </div>
          </div>
          
          <div class="quiz-category">
            <div class="category-header">
              <div class="category-icon" style="background: #03a9f4;">☁️</div>
              <div>
                <div class="category-title">Cloud Computing</div>
                <div class="category-description">Découvrez les services cloud et leur déploiement</div>
              </div>
            </div>
            <div class="difficulty-levels">
              <button class="difficulty-btn beginner" onclick="startSpecificQuiz('cloud', 'beginner')">
                <div class="difficulty-name">Débutant</div>
                <div class="difficulty-xp">10 XP par question</div>
              </button>
              <button class="difficulty-btn intermediate" onclick="startSpecificQuiz('cloud', 'intermediate')">
                <div class="difficulty-name">Moyen</div>
                <div class="difficulty-xp">20 XP par question</div>
              </button>
              <button class="difficulty-btn advanced" onclick="startSpecificQuiz('cloud', 'advanced')">
                <div class="difficulty-name">Difficile</div>
                <div class="difficulty-xp">30 XP par question</div>
              </button>
            </div>
          </div>
          
          <div style="text-align: center; margin-top: 30px;">
            <button class="quiz-btn secondary" onclick="backToChatBtn.click()">
              ← Retour au Chat
            </button>
          </div>
        </div>
      `;
      
      chatPage.style.display = 'none';
      quizPage.style.display = 'flex';
    }

    function startSpecificQuiz(category, difficulty) {
      const questions = QUIZ_DATABASE[category][difficulty];
      
      currentQuiz = {
        category: category,
        difficulty: difficulty,
        questions: questions,
        currentQuestion: 0,
        score: 0,
        totalXP: 0
      };
      
      userAnswers = [];
      showQuizQuestion();
    }

    function showQuizQuestion() {
      const quiz = currentQuiz;
      const question = quiz.questions[quiz.currentQuestion];
      
      quizContent.innerHTML = `
        <div class="quiz-header">
          <h2>📝 Quiz ${quiz.category.charAt(0).toUpperCase() + quiz.category.slice(1)} - ${quiz.difficulty}</h2>
          <p>Question ${quiz.currentQuestion + 1} / ${quiz.questions.length}</p>
        </div>
        
        <div class="quiz-progress">
          <div style="height: 5px; background: var(--border-color); border-radius: 5px;">
            <div style="width: ${((quiz.currentQuestion + 1) / quiz.questions.length) * 100}%; height: 100%; background: var(--primary-color); border-radius: 5px;"></div>
          </div>
        </div>
        
        <div class="quiz-question">
          <h3 style="margin-bottom: 20px;">${question.question}</h3>
          <div class="quiz-options">
            ${question.options.map((option, index) => `
              <button class="quiz-option ${userAnswers[quiz.currentQuestion] === index ? 'selected' : ''}" 
                      data-index="${index}"
                      onclick="selectAnswer(${index})">
                ${option}
              </button>
            `).join('')}
          </div>
          <div style="margin-top: 15px; font-size: 14px; color: var(--text-secondary);">
            XP potentielle: ${question.xp} points
          </div>
        </div>
        
        <div class="quiz-navigation">
          <button class="quiz-btn secondary" onclick="previousQuestion()" ${quiz.currentQuestion === 0 ? 'disabled style="opacity: 0.5;"' : ''}>
            ← Précédent
          </button>
          
          ${quiz.currentQuestion < quiz.questions.length - 1 ? `
            <button class="quiz-btn" onclick="nextQuestion()" ${userAnswers[quiz.currentQuestion] === undefined ? 'disabled style="opacity: 0.5;"' : ''}>
              Suivant →
            </button>
          ` : `
            <button class="quiz-btn" onclick="finishQuiz()" ${userAnswers[quiz.currentQuestion] === undefined ? 'disabled style="opacity: 0.5;"' : ''}>
              Terminer le quiz
            </button>
          `}
        </div>
      `;
    }

    function selectAnswer(index) {
      userAnswers[currentQuiz.currentQuestion] = index;
      showQuizQuestion();
    }

    function previousQuestion() {
      if (currentQuiz.currentQuestion > 0) {
        currentQuiz.currentQuestion--;
        showQuizQuestion();
      }
    }

    function nextQuestion() {
      if (currentQuiz.currentQuestion < currentQuiz.questions.length - 1 && userAnswers[currentQuiz.currentQuestion] !== undefined) {
        currentQuiz.currentQuestion++;
        showQuizQuestion();
      }
    }

    function finishQuiz() {
      let score = 0;
      let totalXP = 0;
      
      currentQuiz.questions.forEach((question, index) => {
        if (userAnswers[index] === question.correct) {
          score++;
          totalXP += question.xp;
        }
      });
      
      currentQuiz.score = score;
      currentQuiz.totalXP = totalXP;
      
      const percentage = Math.round((score / currentQuiz.questions.length) * 100);
      let message = "";
      
      if (percentage >= 90) {
        message = "🎉 Excellent ! Vous êtes un expert !";
      } else if (percentage >= 70) {
        message = "👍 Très bon score !";
      } else if (percentage >= 50) {
        message = "😊 Bon score ! Continuez à apprendre.";
      } else {
        message = "📚 Continuez à utiliser Chelles Project pour améliorer vos connaissances !";
      }
      
      quizContent.innerHTML = `
        <div class="quiz-results">
          <h2>🎯 Résultats du Quiz</h2>
          <div class="score-circle">
            <span style="font-size: 32px;">${score}/${currentQuiz.questions.length}</span>
            <span style="font-size: 16px;">${percentage}%</span>
          </div>
          <p class="score-text">${message}</p>
          <p class="score-text" style="color: var(--primary-color);">Vous avez gagné ${totalXP} XP !</p>
          
          <div style="text-align: left; max-width: 600px; margin: 20px auto;">
            <h3 style="margin-bottom: 15px;">Détail des réponses :</h3>
            ${currentQuiz.questions.map((question, index) => {
              const userAnswer = userAnswers[index];
              const isCorrect = userAnswer === question.correct;
              return `
                <div style="margin-bottom: 20px; padding: 15px; background: ${isCorrect ? 'rgba(76, 175, 80, 0.1)' : 'rgba(244, 67, 54, 0.1)'}; border-radius: var(--radius); border-left: 4px solid ${isCorrect ? '#4CAF50' : '#f44336'};">
                  <p><strong>Question ${index + 1}:</strong> ${question.question}</p>
                  <p style="margin-top: 8px; color: ${isCorrect ? '#4CAF50' : '#f44336'}">
                    ${isCorrect ? '✓' : '✗'} Votre réponse: ${question.options[userAnswer]}
                  </p>
                  ${!isCorrect ? `
                    <p style="margin-top: 8px; color: #4CAF50;">
                      ✓ Réponse correcte: ${question.options[question.correct]}
                    </p>
                  ` : ''}
                  <p style="margin-top: 8px; font-size: 14px; color: var(--text-secondary);">
                    💡 ${question.explanation}
                  </p>
                </div>
              `;
            }).join('')}
          </div>
          
          <button class="back-to-chat-btn" onclick="backToChatBtn.click()">
            ← Retour au Chat
          </button>
          <button class="quiz-btn" onclick="showQuizSelection()" style="margin-left: 10px;">
            🔄 Nouveau Quiz
          </button>
        </div>
      `;
      
      saveQuizResult(score, percentage, totalXP);
    }

    function saveQuizResult(score, percentage, xpEarned) {
      if (!currentUser) return;
      
      const result = {
        userId: `${currentUser.firstName} ${currentUser.lastName}`,
        category: currentQuiz.category,
        difficulty: currentQuiz.difficulty,
        score: score,
        total: currentQuiz.questions.length,
        percentage: percentage,
        xpEarned: xpEarned,
        date: new Date().toISOString()
      };
      
      quizResults.push(result);
      localStorage.setItem('chellesProjectQuizResults', JSON.stringify(quizResults));
    }

    // ===== SYSTEME DE COURS =====
    coursesBtn.addEventListener('click', function() {
      showCourses();
    });

    function showCourses() {
      coursesContent.innerHTML = `
        <div class="courses-header">
          <h2>📚 Cours d'Informatique - Bases Fondamentales</h2>
          <button class="close-courses-btn" id="closeCoursesBtn">×</button>
        </div>
        
        <div class="courses-intro">
          <p>Découvrez nos cours complets sur les technologies informatiques essentielles. Chaque cours présente les concepts fondamentaux avec des explications détaillées.</p>
          <p style="margin-top: 10px; color: var(--primary-color); font-weight: 500;">Téléchargez chaque cours en PDF pour l'étudier hors ligne !</p>
        </div>
        
        <div class="courses-grid">
          ${Object.entries(COURSES_DATABASE).map(([key, course]) => `
            <div class="course-card">
              <div class="course-header" style="background: linear-gradient(135deg, ${course.color}, ${course.color}99);">
                <div class="course-icon">${course.icon}</div>
                <div class="course-title">${course.title}</div>
                <div class="course-description">${course.description}</div>
              </div>
              <div class="course-content">
                ${course.content}
              </div>
              <div class="course-actions">
                <button class="download-btn" onclick="downloadCoursePDF('${key}')">
                  <span>📥</span> Télécharger en PDF
                </button>
              </div>
            </div>
          `).join('')}
        </div>
        
        <div style="text-align: center; margin-top: 30px; color: var(--text-secondary); font-size: 14px;">
          <p>Ces cours sont régulièrement mis à jour avec les dernières technologies et bonnes pratiques.</p>
        </div>
      `;
      
      coursesModal.style.display = 'flex';
      
      document.getElementById('closeCoursesBtn').addEventListener('click', function() {
        coursesModal.style.display = 'none';
      });
    }

    // ===== FONCTION DE TÉLÉCHARGEMENT PDF =====
    function downloadCoursePDF(courseKey) {
      const course = COURSES_DATABASE[courseKey];
      
      // Créer le contenu HTML pour le PDF
      const htmlContent = `
        <!DOCTYPE html>
        <html>
        <head>
          <meta charset="UTF-8">
          <title>${course.title} - Chelles Project</title>
          <style>
            body { font-family: Arial, sans-serif; line-height: 1.6; color: #333; max-width: 800px; margin: 0 auto; padding: 20px; }
            .header { text-align: center; padding: 30px; background: linear-gradient(135deg, ${course.color}, ${course.color}99); color: white; border-radius: 10px; margin-bottom: 30px; }
            .title { font-size: 28px; font-weight: bold; margin-bottom: 10px; }
            .description { font-size: 16px; opacity: 0.9; }
            .section { margin-bottom: 25px; padding-bottom: 15px; border-bottom: 1px solid #eee; }
            .section h3 { color: ${course.color}; font-size: 20px; margin-bottom: 10px; }
            .section p { margin-bottom: 10px; }
            .section ul { padding-left: 20px; }
            .section li { margin-bottom: 8px; }
            .footer { text-align: center; margin-top: 40px; padding-top: 20px; border-top: 2px solid #eee; color: #666; font-size: 12px; }
          </style>
        </head>
        <body>
          <div class="header">
            <div style="font-size: 48px; margin-bottom: 15px;">${course.icon}</div>
            <div class="title">${course.title}</div>
            <div class="description">${course.description}</div>
            <div style="margin-top: 15px; font-size: 14px;">Chelles Project - ${new Date().toLocaleDateString('fr-FR')}</div>
          </div>
          
          ${course.content.replace(/<h4>/g, '<h3>').replace(/<\/h4>/g, '</h3>').replace(/course-section/g, 'section')}
          
          <div class="footer">
            <p>© ${new Date().getFullYear()} Chelles Project - Tous droits réservés</p>
            <p>Document généré le ${new Date().toLocaleString('fr-FR')}</p>
            <p>Pour plus de ressources : Utilisez le chatbot Chelles Project</p>
          </div>
        </body>
        </html>
      `;
      
      // Créer un blob HTML
      const blob = new Blob([htmlContent], { type: 'text/html' });
      const url = URL.createObjectURL(blob);
      
      // Créer un lien pour télécharger
      const link = document.createElement('a');
      link.href = url;
      link.download = `Cours_${course.title.replace(/\s+/g, '_')}_Chelles_Project_${new Date().toISOString().split('T')[0]}.html`;
      
      // Ajouter au document et cliquer
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
      
      // Libérer l'URL
      setTimeout(() => URL.revokeObjectURL(url), 100);
      
      // Afficher une confirmation
      alert(`✅ Le cours "${course.title}" est en cours de téléchargement !\n\nIl sera sauvegardé au format HTML que vous pourrez ouvrir dans n'importe quel navigateur ou convertir en PDF.`);
    }

    // ===== HISTORIQUE =====
    historyBtn.addEventListener('click', function() {
      loadHistory();
      historyModal.style.display = 'flex';
    });

    closeHistoryBtn.addEventListener('click', function() {
      historyModal.style.display = 'none';
    });

    clearHistoryBtn.addEventListener('click', function() {
      if (confirm("Voulez-vous vraiment effacer tout l'historique ? Cette action est irréversible.")) {
        chatHistory = [];
        localStorage.setItem('chellesProjectChatHistory', JSON.stringify(chatHistory));
        loadHistory();
      }
    });

    exportHistoryBtn.addEventListener('click', function() {
      exportHistoryToCSV();
    });

    function loadHistory() {
      historyList.innerHTML = '';
      
      if (chatHistory.length === 0) {
        historyList.innerHTML = '<p style="text-align: center; color: var(--text-secondary); padding: 40px;">Aucun historique disponible.</p>';
        return;
      }
      
      const userHistory = chatHistory.filter(entry => 
        entry.userId === (currentUser ? `${currentUser.firstName} ${currentUser.lastName}` : '')
      );
      
      if (userHistory.length === 0) {
        historyList.innerHTML = '<p style="text-align: center; color: var(--text-secondary); padding: 40px;">Aucun historique pour cet utilisateur.</p>';
        return;
      }
      
      userHistory.forEach((entry, index) => {
        const historyItem = document.createElement('div');
        historyItem.className = 'history-item-full';
        
        const date = new Date(entry.timestamp).toLocaleString('fr-FR');
        
        historyItem.innerHTML = `
          <div class="history-item-header">
            <span>Conversation #${index + 1}</span>
            <span>${date}</span>
          </div>
          <div class="history-user-message">
            <strong>Vous:</strong> ${entry.userMessage}
          </div>
          <div class="history-bot-message">
            <strong>Chelles Project:</strong> ${entry.botResponse.replace(/<[^>]*>/g, '')}
          </div>
        `;
        
        historyList.appendChild(historyItem);
      });
    }

    function addToHistory(userMessage, botResponse) {
      if (!currentUser) return;
      
      const historyEntry = {
        userId: `${currentUser.firstName} ${currentUser.lastName}`,
        userMessage: userMessage,
        botResponse: botResponse,
        timestamp: new Date().toISOString()
      };
      
      chatHistory.push(historyEntry);
      localStorage.setItem('chellesProjectChatHistory', JSON.stringify(chatHistory));
    }

    function exportHistoryToCSV() {
      if (chatHistory.length === 0) {
        alert("L'historique est vide !");
        return;
      }
      
      const userHistory = chatHistory.filter(entry => 
        entry.userId === (currentUser ? `${currentUser.firstName} ${currentUser.lastName}` : '')
      );
      
      if (userHistory.length === 0) {
        alert("Aucun historique à exporter pour cet utilisateur.");
        return;
      }
      
      let csv = "Date,Utilisateur,Question,Réponse\n";
      userHistory.forEach(entry => {
        const date = new Date(entry.timestamp).toLocaleString('fr-FR');
        const user = entry.userId;
        const question = entry.userMessage.replace(/"/g, '""');
        const answer = entry.botResponse.replace(/<[^>]*>/g, '').replace(/"/g, '""');
        
        csv += `"${date}","${user}","${question}","${answer}"\n`;
      });
      
      const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
      const url = URL.createObjectURL(blob);
      const link = document.createElement('a');
      link.href = url;
      link.download = `historique_chelles_project_${new Date().toISOString().split('T')[0]}.csv`;
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }

    // ===== ADMIN SYSTEM =====
    adminBtn.addEventListener('click', function() {
      showPasswordPrompt();
    });

    function showPasswordPrompt() {
      adminContent.innerHTML = `
        <div class="admin-header">
          <h2>🔐 Espace Administrateur</h2>
          <button class="close-history-btn" id="closeAdminBtn">×</button>
        </div>
        <div class="password-form">
          <h3>Accès sécurisé</h3>
          <p>Veuillez entrer le mot de passe administrateur :</p>
          <div style="position: relative;">
            <input type="password" class="password-input" id="adminPassword" placeholder="Mot de passe" autocomplete="off">
            <button id="togglePassword" style="position: absolute; right: 10px; top: 50%; transform: translateY(-50%); background: none; border: none; cursor: pointer; color: var(--text-secondary);">
              👁️
            </button>
          </div>
          <button class="password-submit" id="submitPassword">Accéder</button>
          <div class="password-error" id="passwordError">
            ❌ Mot de passe incorrect
          </div>
        </div>
      `;
      
      adminModal.style.display = 'flex';
      
      document.getElementById('submitPassword').addEventListener('click', checkAdminPassword);
      document.getElementById('adminPassword').addEventListener('keypress', function(e) {
        if (e.key === 'Enter') checkAdminPassword();
      });
      document.getElementById('closeAdminBtn').addEventListener('click', function() {
        adminModal.style.display = 'none';
      });
      
      document.getElementById('togglePassword').addEventListener('click', function() {
        const passwordInput = document.getElementById('adminPassword');
        if (passwordInput.type === 'password') {
          passwordInput.type = 'text';
          this.textContent = '🙈';
        } else {
          passwordInput.type = 'password';
          this.textContent = '👁️';
        }
      });
    }

    function checkAdminPassword() {
      const password = document.getElementById('adminPassword').value;
      const errorElement = document.getElementById('passwordError');
      
      if (password === ADMIN_PASSWORD) {
        errorElement.style.display = 'none';
        showAdminDashboard();
      } else {
        errorElement.style.display = 'block';
      }
    }

    function showAdminDashboard() {
      const stats = calculateAdminStats();
      
      adminContent.innerHTML = `
        <div class="admin-header">
          <h2>📊 Tableau de Bord Administrateur</h2>
          <button class="close-history-btn" id="closeAdminBtn">×</button>
        </div>
        
        <div class="admin-stats-grid">
          <div class="stat-card">
            <div class="stat-value">${stats.totalUsers}</div>
            <div class="stat-label">Utilisateurs uniques</div>
          </div>
          <div class="stat-card">
            <div class="stat-value">${stats.totalConversations}</div>
            <div class="stat-label">Conversations</div>
          </div>
          <div class="stat-card">
            <div class="stat-value">${stats.totalQuizAttempts}</div>
            <div class="stat-label">Quiz réalisés</div>
          </div>
          <div class="stat-card">
            <div class="stat-value">${stats.totalExamenAttempts}</div>
            <div class="stat-label">Examens passés</div>
          </div>
          <div class="stat-card">
            <div class="stat-value">${stats.averageQuizScore}%</div>
            <div class="stat-label">Score moyen quiz</div>
          </div>
          <div class="stat-card">
            <div class="stat-value">${stats.averageExamenScore}%</div>
            <div class="stat-label">Score moyen examen</div>
          </div>
        </div>
        
        <div class="charts-container">
          <div class="chart-box">
            <div class="chart-title">📈 Activité des utilisateurs</div>
            <canvas class="chart-canvas" id="activityChart"></canvas>
          </div>
          <div class="chart-box">
            <div class="chart-title">🎯 Scores aux examens</div>
            <canvas class="chart-canvas" id="scoreChart"></canvas>
          </div>
        </div>
        
        <div style="margin-top: 30px;">
          <h3>👥 Liste des utilisateurs avec badges</h3>
          <div style="max-height: 300px; overflow-y: auto; margin-top: 15px;">
            <table class="users-table">
              <thead>
                <tr>
                  <th>Nom</th>
                  <th>Quiz réussis</th>
                  <th>Examens réussis</th>
                  <th>Badges</th>
                  <th>Dernière activité</th>
                </tr>
              </thead>
              <tbody id="usersTableBody">
                ${stats.usersTableRows}
              </tbody>
            </table>
          </div>
        </div>
        
        <div class="admin-actions">
          <button class="admin-action-btn export" id="exportAllData">
            📥 Exporter toutes les données
          </button>
          <button class="admin-action-btn reset" id="resetAllData">
            🗑️ Réinitialiser toutes les données
          </button>
        </div>
      `;
      
      document.getElementById('closeAdminBtn').addEventListener('click', function() {
        adminModal.style.display = 'none';
      });
      
      document.getElementById('exportAllData').addEventListener('click', exportAllData);
      document.getElementById('resetAllData').addEventListener('click', resetAllData);
      
      setTimeout(() => {
        generateCharts(stats);
      }, 100);
    }

    function calculateAdminStats() {
      const userStats = {};
      
      // Traiter l'historique des conversations
      chatHistory.forEach(entry => {
        if (!userStats[entry.userId]) {
          userStats[entry.userId] = {
            name: entry.userId,
            conversations: 0,
            quizAttempts: 0,
            quizScores: [],
            examenAttempts: 0,
            examenScores: [],
            badges: [],
            lastActivity: entry.timestamp
          };
        }
        userStats[entry.userId].conversations++;
        if (new Date(entry.timestamp) > new Date(userStats[entry.userId].lastActivity)) {
          userStats[entry.userId].lastActivity = entry.timestamp;
        }
      });
      
      // Traiter les résultats de quiz
      quizResults.forEach(result => {
        if (!userStats[result.userId]) {
          userStats[result.userId] = {
            name: result.userId,
            conversations: 0,
            quizAttempts: 0,
            quizScores: [],
            examenAttempts: 0,
            examenScores: [],
            badges: [],
            lastActivity: result.date
          };
        }
        userStats[result.userId].quizAttempts++;
        userStats[result.userId].quizScores.push(result.percentage);
        if (new Date(result.date) > new Date(userStats[result.userId].lastActivity)) {
          userStats[result.userId].lastActivity = result.date;
        }
      });
      
      // Traiter les résultats d'examen
      examenResults.forEach(result => {
        if (!userStats[result.userId]) {
          userStats[result.userId] = {
            name: result.userId,
            conversations: 0,
            quizAttempts: 0,
            quizScores: [],
            examenAttempts: 0,
            examenScores: [],
            badges: [],
            lastActivity: result.date
          };
        }
        userStats[result.userId].examenAttempts++;
        userStats[result.userId].examenScores.push(result.percentage);
        if (result.passed && !userStats[result.userId].badges.includes('expert')) {
          userStats[result.userId].badges.push('expert');
        }
        if (new Date(result.date) > new Date(userStats[result.userId].lastActivity)) {
          userStats[result.userId].lastActivity = result.date;
        }
      });
      
      // Ajouter les badges du localStorage
      Object.entries(badges).forEach(([userId, userBadges]) => {
        if (userStats[userId]) {
          userStats[userId].badges = [...new Set([...userStats[userId].badges, ...userBadges])];
        }
      });
      
      const totalUsers = Object.keys(userStats).length;
      const totalConversations = chatHistory.length;
      const totalQuizAttempts = quizResults.length;
      const totalExamenAttempts = examenResults.length;
      
      let totalQuizScore = 0;
      quizResults.forEach(result => {
        totalQuizScore += result.percentage;
      });
      const averageQuizScore = totalQuizAttempts > 0 ? Math.round(totalQuizScore / totalQuizAttempts) : 0;
      
      let totalExamenScore = 0;
      examenResults.forEach(result => {
        totalExamenScore += result.percentage;
      });
      const averageExamenScore = totalExamenAttempts > 0 ? Math.round(totalExamenScore / totalExamenAttempts) : 0;
      
      let usersTableRows = '';
      Object.values(userStats).forEach(user => {
        const avgQuizScore = user.quizScores.length > 0 
          ? Math.round(user.quizScores.reduce((a, b) => a + b, 0) / user.quizScores.length)
          : 0;
        
        const avgExamenScore = user.examenScores.length > 0 
          ? Math.round(user.examenScores.reduce((a, b) => a + b, 0) / user.examenScores.length)
          : 0;
        
        const lastActivity = new Date(user.lastActivity).toLocaleDateString('fr-FR');
        const badgesDisplay = user.badges.map(b => b === 'expert' ? '🏆' : '🎖️').join(' ');
        
        usersTableRows += `
          <tr>
            <td>${user.name}</td>
            <td>${user.quizAttempts} (${avgQuizScore}%)</td>
            <td>${user.examenAttempts} (${avgExamenScore}%)</td>
            <td>${badgesDisplay || 'Aucun'}</td>
            <td>${lastActivity}</td>
          </tr>
        `;
      });
      
      // Données pour les graphiques
      const last7Days = [];
      for (let i = 6; i >= 0; i--) {
        const date = new Date();
        date.setDate(date.getDate() - i);
        last7Days.push(date.toLocaleDateString('fr-FR', { weekday: 'short' }));
      }
      
      const activityData = Array(7).fill(0);
      [...chatHistory, ...quizResults, ...examenResults].forEach(entry => {
        const entryDate = new Date(entry.date || entry.timestamp);
        const today = new Date();
        const diffTime = Math.abs(today - entryDate);
        const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
        if (diffDays <= 7) {
          activityData[7 - diffDays]++;
        }
      });
      
      const scoreCategories = ['0-20%', '21-40%', '41-60%', '61-80%', '81-100%'];
      const scoreData = [0, 0, 0, 0, 0];
      examenResults.forEach(result => {
        if (result.percentage <= 20) scoreData[0]++;
        else if (result.percentage <= 40) scoreData[1]++;
        else if (result.percentage <= 60) scoreData[2]++;
        else if (result.percentage <= 80) scoreData[3]++;
        else scoreData[4]++;
      });
      
      return {
        totalUsers,
        totalConversations,
        totalQuizAttempts,
        totalExamenAttempts,
        averageQuizScore,
        averageExamenScore,
        usersTableRows,
        chartData: {
          labels: last7Days,
          activityData,
          scoreCategories,
          scoreData
        }
      };
    }

    function generateCharts(stats) {
      // Graphique d'activité
      const activityCtx = document.getElementById('activityChart').getContext('2d');
      if (activityCtx) {
        new Chart(activityCtx, {
          type: 'line',
          data: {
            labels: stats.chartData.labels,
            datasets: [{
              label: 'Activité par jour',
              data: stats.chartData.activityData,
              borderColor: '#9b59b6',
              backgroundColor: 'rgba(155, 89, 182, 0.1)',
              borderWidth: 2,
              fill: true,
              tension: 0.4
            }]
          },
          options: {
            responsive: true,
            maintainAspectRatio: false,
            scales: {
              y: {
                beginAtZero: true,
                ticks: {
                  stepSize: 1
                }
              }
            },
            plugins: {
              legend: {
                display: false
              }
            }
          }
        });
      }
      
      // Graphique des scores
      const scoreCtx = document.getElementById('scoreChart').getContext('2d');
      if (scoreCtx) {
        new Chart(scoreCtx, {
          type: 'bar',
          data: {
            labels: stats.chartData.scoreCategories,
            datasets: [{
              label: 'Nombre d\'examens',
              data: stats.chartData.scoreData,
              backgroundColor: [
                'rgba(244, 67, 54, 0.7)',
                'rgba(255, 193, 7, 0.7)',
                'rgba(76, 175, 80, 0.7)',
                'rgba(33, 150, 243, 0.7)',
                'rgba(156, 39, 176, 0.7)'
              ],
              borderColor: [
                '#f44336',
                '#ffc107',
                '#4CAF50',
                '#2196F3',
                '#9C27B0'
              ],
              borderWidth: 1
            }]
          },
          options: {
            responsive: true,
            maintainAspectRatio: false,
            scales: {
              y: {
                beginAtZero: true,
                ticks: {
                  stepSize: 1
                }
              }
            },
            plugins: {
              legend: {
                display: false
              }
            }
          }
        });
      }
    }

    function exportAllData() {
      const allData = {
        exportDate: new Date().toISOString(),
        chatHistory: chatHistory,
        quizResults: quizResults,
        examenResults: examenResults,
        badges: badges,
        currentUser: currentUser
      };
      
      const dataStr = JSON.stringify(allData, null, 2);
      const blob = new Blob([dataStr], { type: 'application/json' });
      const url = URL.createObjectURL(blob);
      const link = document.createElement('a');
      link.href = url;
      link.download = `chelles_project_full_data_${new Date().toISOString().split('T')[0]}.json`;
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }

    function resetAllData() {
      if (confirm("⚠️ ATTENTION : Cette action va supprimer TOUTES les données (historique, quiz, examens, badges). Cette action est irréversible. Continuer ?")) {
        localStorage.clear();
        chatHistory = [];
        quizResults = [];
        examenResults = [];
        badges = {};
        currentUser = null;
        alert("✅ Toutes les données ont été réinitialisées. La page va se recharger.");
        setTimeout(() => {
          location.reload();
        }, 1000);
      }
    }

    // ===== FONCTIONNALITÉS DU CHATBOT =====
    const chatMessages = document.getElementById('chatMessages');
    const chatInput = document.getElementById('chatInput');
    const sendButton = document.getElementById('sendButton');
    const newChatBtn = document.getElementById('newChatBtn');

    function addMessage(text, sender) {
      const messageDiv = document.createElement('div');
      messageDiv.className = 'message ' + (sender === 'user' ? 'user-message' : 'bot');
      
      const avatarDiv = document.createElement('div');
      avatarDiv.className = 'avatar ' + (sender === 'user' ? 'user-avatar' : 'bot-avatar');
      avatarDiv.textContent = sender === 'user' ? 'U' : 'CP';
      
      const contentDiv = document.createElement('div');
      contentDiv.className = 'message-content';
      contentDiv.innerHTML = text;
      
      messageDiv.appendChild(avatarDiv);
      messageDiv.appendChild(contentDiv);
      
      if (sender === 'user') {
        const suggestions = document.querySelector('.suggestions');
        const existingUserMessages = document.querySelectorAll('.message.user-message');
        if (suggestions && existingUserMessages.length === 0) {
          suggestions.remove();
        }
      }
      
      chatMessages.appendChild(messageDiv);
      chatMessages.scrollTop = chatMessages.scrollHeight;
    }

    function sendMessage() {
      const text = chatInput.value.trim();
      if (!text) return;
      
      addMessage(text, 'user');
      chatInput.value = '';
      
      setTimeout(() => {
        const botResponse = getAnswer(text);
        addMessage(botResponse, 'bot');
        addToHistory(text, botResponse);
      }, 300);
    }

    function newConversation() {
      chatMessages.innerHTML = `
        <div class="message bot">
          <div class="avatar bot-avatar">CP</div>
          <div class="message-content">
            👋 Salut <span id="userFirstName">${userFirstName.textContent}</span> ! Je suis <strong>Chelles Project</strong>, ton assistant d'informatique. Pose-moi une question sur les réseaux, le matériel, la sécurité ou la programmation.
          </div>
        </div>
        <div class="suggestions">
          <div class="suggestion-card">
            <h3>Explique-moi les réseaux</h3>
            <p>Concepts fondamentaux et protocoles</p>
          </div>
          <div class="suggestion-card">
            <h3>Conseils en cybersécurité</h3>
            <p>Protection et bonnes pratiques</p>
          </div>
          <div class="suggestion-card">
            <h3>Concepts de cloud</h3>
            <p>Services et déploiement</p>
          </div>
          <div class="suggestion-card">
            <h3>Data Science</h3>
            <p>Analyse et machine learning</p>
          </div>
        </div>
      `;
      chatInput.value = '';
      attachSuggestionEvents();
    }

    function attachSuggestionEvents() {
      document.querySelectorAll('.suggestion-card').forEach(card => {
        card.addEventListener('click', function() {
          const question = this.querySelector('h3').textContent;
          chatInput.value = question;
          sendMessage();
        });
      });
    }

    sendButton.addEventListener('click', sendMessage);
    chatInput.addEventListener('keypress', function(e) {
      if (e.key === 'Enter' && !e.shiftKey) {
        e.preventDefault();
        sendMessage();
      }
    });
    newChatBtn.addEventListener('click', newConversation);
    attachSuggestionEvents();

    // ===== FONCTIONS GLOBALES =====
    window.selectAnswer = selectAnswer;
    window.previousQuestion = previousQuestion;
    window.nextQuestion = nextQuestion;
    window.finishQuiz = finishQuiz;
    window.startSpecificQuiz = startSpecificQuiz;
    window.downloadCoursePDF = downloadCoursePDF;
    window.selectExamenAnswer = selectExamenAnswer;
    window.previousExamenQuestion = previousExamenQuestion;
    window.nextExamenQuestion = nextExamenQuestion;
    window.startExamen = startExamen;

    // ===== FONCTION getAnswer =====
    function getAnswer(message) {
      const lowerMessage = message.toLowerCase();

      if (lowerMessage.includes('réseau')) return "🌐 <strong>Réseau informatique</strong> : ensemble d'appareils reliés pour partager des données et des ressources. Il existe différents types de réseaux : <br> - LAN : local (maison, entreprise) <br> - WAN : étendu (Internet) <br> - WLAN : sans fil (Wi-Fi).";
      if (lowerMessage.includes('ip')) return "🌍 <strong>Adresse IP</strong> : identifiant numérique unique attribué à chaque appareil sur un réseau. Deux versions existent : IPv4 (ex. 192.168.1.1) et IPv6 (ex. 2001:db8::1).";
      if (lowerMessage.includes('dns')) return "📡 <strong>DNS</strong> (Domain Name System) traduit un nom de domaine (ex. google.com) en adresse IP, permettant de naviguer sur Internet facilement.";
      if (lowerMessage.includes('tcp')) return "📨 <strong>TCP</strong> (Transmission Control Protocol) assure la fiabilité des échanges réseau en vérifiant que les paquets arrivent dans le bon ordre.";
      if (lowerMessage.includes('udp')) return "⚡ <strong>UDP</strong> (User Datagram Protocol) est plus rapide mais sans vérification. Utilisé pour le streaming et les jeux en ligne.";
      if (lowerMessage.includes('cpu')) return "⚙️ <strong>CPU</strong> (Central Processing Unit) exécute les instructions. Sa puissance dépend de la fréquence (GHz) et du nombre de cœurs.";
      if (lowerMessage.includes('ram')) return "💾 <strong>RAM</strong> : mémoire temporaire ultra rapide. Plus il y en a, plus le système peut exécuter de programmes simultanément.";
      if (lowerMessage.includes('ssd')) return "⚡ <strong>SSD</strong> : support de stockage à mémoire flash, jusqu'à 10x plus rapide qu'un disque dur.";
      if (lowerMessage.includes('python')) return "🐍 <strong>Python</strong> : langage de programmation simple et puissant. Utilisé pour le web, la data science, l'IA et l'automatisation.";
      if (lowerMessage.includes('javascript')) return "📜 <strong>JavaScript</strong> : langage du web, permet de rendre les sites interactifs. Utilisé avec HTML et CSS.";
      if (lowerMessage.includes('firewall') || lowerMessage.includes('pare-feu')) return "🛡️ <strong>Pare-feu</strong> : filtre le trafic réseau et bloque les connexions non autorisées.";
      if (lowerMessage.includes('virus')) return "🦠 <strong>Virus informatique</strong> : programme malveillant conçu pour altérer ou voler des données.";
      if (lowerMessage.includes('vpn')) return "🕵️ <strong>VPN</strong> : crée un tunnel chiffré entre toi et Internet, protégeant ta vie privée.";
      if (lowerMessage.includes('ia')) return "🤖 <strong>Intelligence artificielle</strong> : discipline qui cherche à créer des programmes capables de simuler le raisonnement humain.";
      if (lowerMessage.includes('machine learning')) return "📊 <strong>Machine Learning</strong> : technique d'IA où les ordinateurs apprennent à partir de données pour faire des prédictions.";
      if (lowerMessage.includes('bonjour')) return "👋 Bonjour ! Comment vas-tu aujourd'hui ?";
      if (lowerMessage.includes('salut')) return "😄 Salut à toi ! Ça fait plaisir de te voir ici.";
      if (lowerMessage.includes('merci')) return "🙏 Avec plaisir ! Je suis là pour ça 😄";
      
      // ========== RÉSEAUX ==========
      if (lowerMessage.includes('réseau')) return "🌐 <strong>Réseau informatique</strong> : ensemble d'appareils reliés pour partager des données et des ressources. Il existe différents types de réseaux : <br> - LAN : local (maison, entreprise) <br> - WAN : étendu (Internet) <br> - WLAN : sans fil (Wi-Fi).";
      if (lowerMessage.includes('ip')) return "🌍 <strong>Adresse IP</strong> : identifiant numérique unique attribué à chaque appareil sur un réseau. Deux versions existent : IPv4 (ex. 192.168.1.1) et IPv6 (ex. 2001:db8::1).";
      if (lowerMessage.includes('dns')) return "📡 <strong>DNS</strong> (Domain Name System) traduit un nom de domaine (ex. google.com) en adresse IP, permettant de naviguer sur Internet facilement.";
      if (lowerMessage.includes('tcp')) return "📨 <strong>TCP</strong> (Transmission Control Protocol) assure la fiabilité des échanges réseau en vérifiant que les paquets arrivent dans le bon ordre.";
      if (lowerMessage.includes('udp')) return "⚡ <strong>UDP</strong> (User Datagram Protocol) est plus rapide mais sans vérification. Utilisé pour le streaming et les jeux en ligne.";
      if (lowerMessage.includes('http')) return "🌐 <strong>HTTP</strong> est le protocole du Web. Sa version sécurisée HTTPS chiffre les données avec SSL/TLS.";
      if (lowerMessage.includes('ssh')) return "🖥️ <strong>SSH</strong> : permet une connexion chiffrée à distance à un serveur. Très utilisé par les administrateurs systèmes.";

      // ========== MATÉRIEL ==========
      if (lowerMessage.includes('cpu')) return "⚙️ <strong>CPU</strong> (Central Processing Unit) exécute les instructions. Sa puissance dépend de la fréquence (GHz) et du nombre de cœurs.";
      if (lowerMessage.includes('ram')) return "💾 <strong>RAM</strong> : mémoire temporaire ultra rapide. Plus il y en a, plus le système peut exécuter de programmes simultanément.";
      if (lowerMessage.includes('ssd')) return "⚡ <strong>SSD</strong> : support de stockage à mémoire flash, jusqu'à 10x plus rapide qu'un disque dur.";
      if (lowerMessage.includes('gpu')) return "🎮 <strong>GPU</strong> : processeur graphique utilisé pour les jeux, le calcul scientifique et l'IA.";
      if (lowerMessage.includes('bios')) return "🔧 <strong>BIOS/UEFI</strong> : logiciel intégré à la carte mère qui initialise le matériel au démarrage.";

      // ========== PROGRAMMATION ==========
      if (lowerMessage.includes('python')) return "🐍 <strong>Python</strong> : langage de programmation simple et puissant. Utilisé pour le web, la data science, l'IA et l'automatisation.";
      if (lowerMessage.includes('javascript')) return "📜 <strong>JavaScript</strong> : langage du web, permet de rendre les sites interactifs. Utilisé avec HTML et CSS.";
      if (lowerMessage.includes('html')) return "🌐 <strong>HTML</strong> : structure une page web à l'aide de balises comme &lt;div&gt;, &lt;p&gt; et &lt;img&gt;.";
      if (lowerMessage.includes('css')) return "🎨 <strong>CSS</strong> : gère le style (couleurs, tailles, marges) des pages web.";
      if (lowerMessage.includes('java')) return "☕ <strong>Java</strong> : langage orienté objet, très utilisé pour Android et les applications d'entreprise.";
      if (lowerMessage.includes('c++')) return "⚡ <strong>C++</strong> : langage performant pour les systèmes, jeux vidéo et logiciels embarqués.";

      // ========== SÉCURITÉ ==========
      if (lowerMessage.includes('firewall') || lowerMessage.includes('pare-feu')) return "🛡️ <strong>Pare-feu</strong> : filtre le trafic réseau et bloque les connexions non autorisées.";
      if (lowerMessage.includes('virus')) return "🦠 <strong>Virus informatique</strong> : programme malveillant conçu pour altérer ou voler des données.";
      if (lowerMessage.includes('vpn')) return "🕵️ <strong>VPN</strong> : crée un tunnel chiffré entre toi et Internet, protégeant ta vie privée.";
       // ========== RÉSEAUX ==========
  if (lowerMessage.includes('réseau')) return "🌐 <strong>Réseau informatique</strong> : ensemble d’appareils reliés pour partager des données et des ressources. Il existe différents types de réseaux : <br> - LAN : local (maison, entreprise) <br> - WAN : étendu (Internet) <br> - WLAN : sans fil (Wi-Fi).";
  if (lowerMessage.includes('ip')) return "🌍 <strong>Adresse IP</strong> : identifiant numérique unique attribué à chaque appareil sur un réseau. Deux versions existent : IPv4 (ex. 192.168.1.1) et IPv6 (ex. 2001:db8::1).";
  if (lowerMessage.includes('dns')) return "📡 <strong>DNS</strong> (Domain Name System) traduit un nom de domaine (ex. google.com) en adresse IP, permettant de naviguer sur Internet facilement.";
  if (lowerMessage.includes('tcp')) return "📨 <strong>TCP</strong> (Transmission Control Protocol) assure la fiabilité des échanges réseau en vérifiant que les paquets arrivent dans le bon ordre.";
  if (lowerMessage.includes('udp')) return "⚡ <strong>UDP</strong> (User Datagram Protocol) est plus rapide mais sans vérification. Utilisé pour le streaming et les jeux en ligne.";
  if (lowerMessage.includes('http')) return "🌐 <strong>HTTP</strong> est le protocole du Web. Sa version sécurisée HTTPS chiffre les données avec SSL/TLS.";
  if (lowerMessage.includes('ssh')) return "🖥️ <strong>SSH</strong> : permet une connexion chiffrée à distance à un serveur. Très utilisé par les administrateurs systèmes.";

  // ========== MATÉRIEL ==========
  if (lowerMessage.includes('cpu')) return "⚙️ <strong>CPU</strong> (Central Processing Unit) exécute les instructions. Sa puissance dépend de la fréquence (GHz) et du nombre de cœurs.";
  if (lowerMessage.includes('ram')) return "💾 <strong>RAM</strong> : mémoire temporaire ultra rapide. Plus il y en a, plus le système peut exécuter de programmes simultanément.";
  if (lowerMessage.includes('ssd')) return "⚡ <strong>SSD</strong> : support de stockage à mémoire flash, jusqu’à 10x plus rapide qu’un disque dur.";
  if (lowerMessage.includes('gpu')) return "🎮 <strong>GPU</strong> : processeur graphique utilisé pour les jeux, le calcul scientifique et l’IA.";
  if (lowerMessage.includes('bios')) return "🔧 <strong>BIOS/UEFI</strong> : logiciel intégré à la carte mère qui initialise le matériel au démarrage.";

  // ========== PROGRAMMATION ==========
  if (lowerMessage.includes('python')) return "🐍 <strong>Python</strong> : langage de programmation simple et puissant. Utilisé pour le web, la data science, l’IA et l’automatisation.";
  if (lowerMessage.includes('javascript')) return "📜 <strong>JavaScript</strong> : langage du web, permet de rendre les sites interactifs. Utilisé avec HTML et CSS.";
  if (lowerMessage.includes('html')) return "🌐 <strong>HTML</strong> : structure une page web à l’aide de balises comme &lt;div&gt;, &lt;p&gt; et &lt;img&gt;.";
  if (lowerMessage.includes('css')) return "🎨 <strong>CSS</strong> : gère le style (couleurs, tailles, marges) des pages web.";
  if (lowerMessage.includes('java')) return "☕ <strong>Java</strong> : langage orienté objet, très utilisé pour Android et les applications d’entreprise.";
  if (lowerMessage.includes('c++')) return "⚡ <strong>C++</strong> : langage performant pour les systèmes, jeux vidéo et logiciels embarqués.";

  // ========== SÉCURITÉ ==========
  if (lowerMessage.includes('firewall') || lowerMessage.includes('pare-feu')) return "🛡️ <strong>Pare-feu</strong> : filtre le trafic réseau et bloque les connexions non autorisées.";
  if (lowerMessage.includes('virus')) return "🦠 <strong>Virus informatique</strong> : programme malveillant conçu pour altérer ou voler des données.";
  if (lowerMessage.includes('vpn')) return "🕵️ <strong>VPN</strong> : crée un tunnel chiffré entre toi et Internet, protégeant ta vie privée.";
// ========== CYBERSÉCURITÉ ==========

// 1 à 10 : concepts de base
if (lowerMessage.includes('cybersecurite')) return "🛡️ <strong>Cybersécurité</strong> : ensemble des pratiques pour protéger les ordinateurs, réseaux et données contre les attaques.";
if (lowerMessage.includes('virus')) return "🦠 <strong>Virus</strong> : programme malveillant qui se propage et infecte d'autres fichiers ou ordinateurs.";
if (lowerMessage.includes('malware')) return "💀 <strong>Malware</strong> : logiciel malveillant conçu pour endommager ou voler des informations.";
if (lowerMessage.includes('hacker')) return "🧑‍💻 <strong>Hacker</strong> : personne qui cherche à pénétrer un système informatique, parfois pour apprendre, parfois pour nuire.";
if (lowerMessage.includes('phishing')) return "🎣 <strong>Phishing</strong> : technique d’arnaque où un pirate se fait passer pour un service fiable afin de voler des infos personnelles.";
if (lowerMessage.includes('mot de passe')) return "🔑 <strong>Mot de passe</strong> : clé secrète qui protège l’accès à un compte ou à un appareil.";
if (lowerMessage.includes('pare feu') || lowerMessage.includes('firewall')) return "🔥 <strong>Pare-feu</strong> : barrière de sécurité qui filtre les connexions entre un réseau et Internet.";
if (lowerMessage.includes('vpn')) return "🕶️ <strong>VPN</strong> : service qui cache ton adresse IP et chiffre ta connexion pour protéger ta vie privée.";
if (lowerMessage.includes('attaque')) return "⚔️ <strong>Attaque informatique</strong> : tentative de piratage ou d’intrusion dans un système.";
if (lowerMessage.includes('protection')) return "🛡️ <strong>Protection</strong> : ensemble de mesures pour éviter les menaces et sécuriser les données.";

// 11 à 20 : menaces courantes
if (lowerMessage.includes('ransomware')) return "💸 <strong>Ransomware</strong> : virus qui bloque tes fichiers et demande une rançon pour les récupérer.";
if (lowerMessage.includes('spyware')) return "👁️ <strong>Spyware</strong> : logiciel espion qui collecte tes données à ton insu.";
if (lowerMessage.includes('trojan') || lowerMessage.includes('cheval de troie')) return "🐴 <strong>Cheval de Troie</strong> : programme qui se fait passer pour un logiciel légitime mais installe un virus.";
if (lowerMessage.includes('ver')) return "🪱 <strong>Ver informatique</strong> : programme qui se propage automatiquement sans intervention humaine.";
if (lowerMessage.includes('adware')) return "📺 <strong>Adware</strong> : programme qui affiche des publicités non désirées sur ton appareil.";
if (lowerMessage.includes('keylogger')) return "⌨️ <strong>Keylogger</strong> : logiciel qui enregistre tout ce que tu tapes sur ton clavier.";
if (lowerMessage.includes('botnet')) return "🤖 <strong>Botnet</strong> : réseau d’ordinateurs infectés contrôlés par un pirate à distance.";
if (lowerMessage.includes('ddos')) return "🌊 <strong>DDoS</strong> : attaque qui submerge un site de trafic pour le rendre indisponible.";
if (lowerMessage.includes('backdoor')) return "🚪 <strong>Backdoor</strong> : accès caché laissé dans un système pour y revenir facilement.";
if (lowerMessage.includes('zero day')) return "🕒 <strong>Faille Zero-Day</strong> : vulnérabilité inconnue encore non corrigée par les développeurs.";

// 21 à 30 : sécurité des données
if (lowerMessage.includes('donnees')) return "💾 <strong>Données</strong> : informations numériques à protéger contre le vol ou la perte.";
if (lowerMessage.includes('chiffrement')) return "🔐 <strong>Chiffrement</strong> : méthode pour rendre des données illisibles sans clé secrète.";
if (lowerMessage.includes('dechiffrement')) return "🔓 <strong>Déchiffrement</strong> : opération inverse du chiffrement pour rendre les données lisibles.";
if (lowerMessage.includes('authentification')) return "🪪 <strong>Authentification</strong> : vérification de ton identité avant d’accéder à un service.";
if (lowerMessage.includes('double facteur')) return "2️⃣ <strong>Authentification à deux facteurs</strong> : méthode qui ajoute une deuxième étape de vérification pour plus de sécurité.";
if (lowerMessage.includes('identifiant')) return "🧾 <strong>Identifiant</strong> : nom d’utilisateur qui te permet de te connecter à un compte.";
if (lowerMessage.includes('securite reseau')) return "🌐 <strong>Sécurité réseau</strong> : protection des connexions et communications entre ordinateurs.";
if (lowerMessage.includes('fuite de donnees')) return "💧 <strong>Fuite de données</strong> : quand des informations confidentielles sont volées ou rendues publiques.";
if (lowerMessage.includes('cryptographie')) return "🧮 <strong>Cryptographie</strong> : science du secret utilisée pour protéger les messages et données.";
if (lowerMessage.includes('base de donnees')) return "🗃️ <strong>Base de données</strong> : ensemble structuré d’informations stockées qu’il faut protéger.";

// 31 à 40 : comportements et bonnes pratiques
if (lowerMessage.includes('mise a jour')) return "🔁 <strong>Mise à jour</strong> : action d’installer la dernière version d’un logiciel pour corriger des failles.";
if (lowerMessage.includes('sauvegarde')) return "💽 <strong>Sauvegarde</strong> : copie de tes fichiers pour éviter de tout perdre en cas d’attaque.";
if (lowerMessage.includes('wifi public')) return "📶 <strong>Wi-Fi public</strong> : connexion non sécurisée où il faut éviter de se connecter à ses comptes sensibles.";
if (lowerMessage.includes('reseaux sociaux')) return "📱 <strong>Réseaux sociaux</strong> : lieux où il faut faire attention à ce que tu partages pour éviter le vol d’identité.";
if (lowerMessage.includes('ingénierie sociale')) return "🎭 <strong>Ingénierie sociale</strong> : manipulation psychologique pour te pousser à révéler des informations.";
if (lowerMessage.includes('piratage')) return "🕵️ <strong>Piratage</strong> : action d’entrer illégalement dans un système informatique.";
if (lowerMessage.includes('securite informatique')) return "💻 <strong>Sécurité informatique</strong> : ensemble des moyens pour protéger les systèmes et les données.";
if (lowerMessage.includes('cyberattaque')) return "🚨 <strong>Cyberattaque</strong> : attaque menée via Internet pour voler, bloquer ou détruire des données.";
if (lowerMessage.includes('risque')) return "⚠️ <strong>Risque informatique</strong> : possibilité qu’un incident nuise à un système ou à des données.";
if (lowerMessage.includes('bonne pratique')) return "✅ <strong>Bonne pratique</strong> : comportement à adopter pour renforcer la sécurité numérique.";

// 41 à 50 : outils et défenses
if (lowerMessage.includes('antivirus')) return "🧰 <strong>Antivirus</strong> : programme qui détecte et supprime les logiciels malveillants.";
if (lowerMessage.includes('antimalware')) return "🧹 <strong>Antimalware</strong> : outil qui protège contre les virus, vers et autres menaces.";
if (lowerMessage.includes('analyse')) return "🔍 <strong>Analyse de sécurité</strong> : examen d’un système pour trouver des failles ou infections.";
if (lowerMessage.includes('scan')) return "🛰️ <strong>Scan de sécurité</strong> : vérification automatique des fichiers et réseaux.";
if (lowerMessage.includes('pare virus')) return "🦠 <strong>Pare-virus</strong> : outil de prévention contre les infections logicielles.";
if (lowerMessage.includes('firewall materiel')) return "🧱 <strong>Pare-feu matériel</strong> : dispositif physique qui protège un réseau des attaques extérieures.";
if (lowerMessage.includes('securite cloud')) return "☁️ <strong>Sécurité du cloud</strong> : ensemble de mesures pour protéger les données stockées en ligne.";
if (lowerMessage.includes('gestion de mots de passe')) return "🔒 <strong>Gestionnaire de mots de passe</strong> : outil qui stocke et crée des mots de passe forts.";
if (lowerMessage.includes('proxy')) return "🧭 <strong>Proxy</strong> : serveur intermédiaire qui masque ton adresse IP et filtre les connexions.";
if (lowerMessage.includes('email securite')) return "📬 <strong>Sécurité des emails</strong> : ensemble de techniques pour éviter le spam et le phishing.";

// 51 à 60 : notions générales
if (lowerMessage.includes('donnee personnelle')) return "👤 <strong>Donnée personnelle</strong> : information qui permet de t’identifier, comme ton nom ou ton adresse.";
if (lowerMessage.includes('confidentialite')) return "🤫 <strong>Confidentialité</strong> : garantie que tes informations restent privées.";
if (lowerMessage.includes('integrite')) return "⚖️ <strong>Intégrité</strong> : assurance que les données n’ont pas été modifiées ou corrompues.";
if (lowerMessage.includes('disponibilite')) return "🕓 <strong>Disponibilité</strong> : fait que les systèmes soient accessibles quand on en a besoin.";
if (lowerMessage.includes('authenticite')) return "🎟️ <strong>Authenticité</strong> : preuve que les données proviennent bien de la bonne source.";
if (lowerMessage.includes('identite numerique')) return "🪞 <strong>Identité numérique</strong> : ensemble de tes informations personnelles sur Internet.";
if (lowerMessage.includes('regle de securite')) return "📜 <strong>Règle de sécurité</strong> : consigne à suivre pour éviter les failles et les attaques.";
if (lowerMessage.includes('incident')) return "🚧 <strong>Incident de sécurité</strong> : événement qui compromet la sécurité d’un système.";
if (lowerMessage.includes('cybercriminalite')) return "🚔 <strong>Cybercriminalité</strong> : ensemble des crimes commis sur Internet.";
if (lowerMessage.includes('securite numerique')) return "🌍 <strong>Sécurité numérique</strong> : protection de tout ce qui est connecté à Internet.";

  // ========== IA ==========
if (lowerMessage.includes('ia')) return "🤖 <strong>Intelligence artificielle</strong> : discipline qui cherche à créer des programmes capables de simuler le raisonnement humain.";
if (lowerMessage.includes('machine learning')) return "📊 <strong>Machine Learning</strong> : technique d’IA où les ordinateurs apprennent à partir de données pour faire des prédictions.";
if (lowerMessage.includes('neurone')) return "🧠 <strong>Réseaux de neurones</strong> : modèles inspirés du cerveau humain, utilisés dans la reconnaissance vocale, l’image et le texte.";
// ========== AUTRES TERMES IA ==========
  if (lowerMessage.includes('deep learning')) return "🧩 <strong>Deep Learning</strong> : sous-domaine du machine learning utilisant des réseaux de neurones profonds pour traiter de grandes quantités de données.";
  if (lowerMessage.includes('nlp') || lowerMessage.includes('traitement du langage')) return "💬 <strong>Traitement du langage naturel (NLP)</strong> : branche de l’IA qui permet aux machines de comprendre et de générer du texte humain.";
  if (lowerMessage.includes('computer vision') || lowerMessage.includes('vision par ordinateur')) return "👁️ <strong>Vision par ordinateur</strong> : domaine de l’IA qui apprend aux ordinateurs à interpréter et comprendre des images ou des vidéos.";
  if (lowerMessage.includes('chatbot')) return "💡 <strong>Chatbot</strong> : programme d’IA capable de dialoguer avec un utilisateur en langage naturel, comme moi 😄.";
  if (lowerMessage.includes('data science')) return "📈 <strong>Data Science</strong> : discipline qui exploite les données, les statistiques et l’IA pour extraire des informations utiles et faire des prédictions.";
  if (lowerMessage.includes('entrainement')) return "🏋️ <strong>Entraînement d’un modèle</strong> : processus où un modèle d’IA apprend à partir de données pour améliorer ses performances.";
  if (lowerMessage.includes('dataset') || lowerMessage.includes('jeu de données')) return "🗂️ <strong>Dataset</strong> : ensemble de données utilisé pour entraîner, valider ou tester un modèle d’IA.";
  if (lowerMessage.includes('algorithme')) return "⚙️ <strong>Algorithme</strong> : suite d’instructions logiques qu’un ordinateur exécute pour résoudre un problème.";
  if (lowerMessage.includes('biais')) return "🎯 <strong>Biais algorithmique</strong> : déviation ou erreur d’un modèle d’IA causée par des données d’entraînement incomplètes ou déséquilibrées.";
  if (lowerMessage.includes('supervisé')) return "📚 <strong>Apprentissage supervisé</strong> : type d’entraînement où le modèle apprend à partir de données déjà étiquetées.";
  if (lowerMessage.includes('non supervisé')) return "🔍 <strong>Apprentissage non supervisé</strong> : type d’entraînement où le modèle découvre seul des structures ou des regroupements dans les données.";
  if (lowerMessage.includes('reinforcement') || lowerMessage.includes('renforcement')) return "🏆 <strong>Apprentissage par renforcement</strong> : méthode où l’IA apprend en recevant des récompenses ou des pénalités selon ses actions.";
  // ========== CLOUD & DEVOPS ==========

// 1 à 10 : notions de base du cloud
if (lowerMessage.includes('cloud')) return "☁️ <strong>Cloud</strong> : ensemble de serveurs accessibles sur Internet pour stocker, gérer ou exécuter des services.";
if (lowerMessage.includes('stockage cloud')) return "💾 <strong>Stockage cloud</strong> : service qui permet de sauvegarder tes fichiers sur Internet plutôt que sur ton appareil.";
if (lowerMessage.includes('serveur')) return "🖥️ <strong>Serveur</strong> : ordinateur puissant qui héberge des sites web ou des applications.";
if (lowerMessage.includes('cloud computing')) return "⚙️ <strong>Cloud Computing</strong> : utilisation de ressources informatiques (serveurs, stockage, logiciels) à distance via Internet.";
if (lowerMessage.includes('saas')) return "📦 <strong>SaaS</strong> : logiciel accessible en ligne sans installation, comme Gmail ou Canva.";
if (lowerMessage.includes('paas')) return "🧱 <strong>PaaS</strong> : plateforme cloud qui fournit les outils pour développer et déployer des applications.";
if (lowerMessage.includes('iaas')) return "🏗️ <strong>IaaS</strong> : service cloud qui loue des serveurs virtuels et du stockage aux entreprises.";
if (lowerMessage.includes('multi cloud')) return "🌤️ <strong>Multi-cloud</strong> : utilisation de plusieurs fournisseurs cloud pour éviter la dépendance à un seul.";
if (lowerMessage.includes('cloud hybride')) return "🌩️ <strong>Cloud hybride</strong> : combinaison entre cloud public et cloud privé pour plus de flexibilité.";
if (lowerMessage.includes('cloud prive')) return "🔒 <strong>Cloud privé</strong> : infrastructure cloud réservée à une seule entreprise pour plus de contrôle.";

// 11 à 20 : fournisseurs de cloud
if (lowerMessage.includes('aws') || lowerMessage.includes('amazon web services')) return "🟧 <strong>AWS</strong> : plateforme cloud d’Amazon, leader mondial des services en ligne.";
if (lowerMessage.includes('azure')) return "🔷 <strong>Microsoft Azure</strong> : solution cloud de Microsoft pour héberger, développer et gérer des applications.";
if (lowerMessage.includes('google cloud')) return "🟦 <strong>Google Cloud</strong> : plateforme cloud de Google pour le stockage, les applications et l’IA.";
if (lowerMessage.includes('ibm cloud')) return "⚫ <strong>IBM Cloud</strong> : plateforme d’infrastructure et de services cloud d’IBM.";
if (lowerMessage.includes('oracle cloud')) return "🟥 <strong>Oracle Cloud</strong> : services cloud orientés bases de données et entreprises.";
if (lowerMessage.includes('digitalocean')) return "🌊 <strong>DigitalOcean</strong> : fournisseur cloud simple et rapide pour les développeurs.";
if (lowerMessage.includes('ovh')) return "🇫🇷 <strong>OVHcloud</strong> : fournisseur cloud français proposant serveurs, stockage et hébergement web.";
if (lowerMessage.includes('alibaba cloud')) return "🐉 <strong>Alibaba Cloud</strong> : plateforme cloud du groupe Alibaba, très populaire en Asie.";
if (lowerMessage.includes('heroku')) return "🚀 <strong>Heroku</strong> : plateforme PaaS qui facilite le déploiement d’applications web.";
if (lowerMessage.includes('cloudflare')) return "🌐 <strong>Cloudflare</strong> : service qui accélère les sites web et protège contre les attaques.";

// 21 à 30 : outils DevOps essentiels
if (lowerMessage.includes('devops')) return "🧩 <strong>DevOps</strong> : méthode qui rapproche les équipes de développement et d’exploitation pour livrer plus vite et plus sûr.";
if (lowerMessage.includes('ci cd')) return "🔁 <strong>CI/CD</strong> : automatisation du test et du déploiement des applications pour gagner du temps et éviter les erreurs.";
if (lowerMessage.includes('pipeline')) return "⛓️ <strong>Pipeline</strong> : suite d’étapes automatiques pour construire, tester et déployer un logiciel.";
if (lowerMessage.includes('integration continue')) return "🧪 <strong>Intégration continue</strong> : pratique consistant à tester souvent le code pour détecter les erreurs tôt.";
if (lowerMessage.includes('deploiement continu')) return "🚢 <strong>Déploiement continu</strong> : mise à jour automatique des applications sans interruption.";
if (lowerMessage.includes('docker')) return "🐳 <strong>Docker</strong> : outil qui crée des conteneurs pour exécuter les applications de manière isolée.";
if (lowerMessage.includes('kubernetes')) return "☸️ <strong>Kubernetes</strong> : système qui gère et orchestre les conteneurs Docker à grande échelle.";
if (lowerMessage.includes('git')) return "🔧 <strong>Git</strong> : outil de versionnage du code pour suivre les changements et collaborer.";
if (lowerMessage.includes('github')) return "🐙 <strong>GitHub</strong> : plateforme en ligne pour héberger du code et collaborer sur des projets.";
if (lowerMessage.includes('gitlab')) return "🦊 <strong>GitLab</strong> : alternative à GitHub avec des fonctions intégrées de CI/CD.";

// 31 à 40 : infrastructure et automatisation
if (lowerMessage.includes('infrastructure as code')) return "📜 <strong>Infrastructure as Code</strong> : gestion automatique des serveurs avec du code au lieu de tout faire à la main.";
if (lowerMessage.includes('terraform')) return "🌍 <strong>Terraform</strong> : outil pour créer et gérer l’infrastructure cloud avec du code.";
if (lowerMessage.includes('ansible')) return "🤖 <strong>Ansible</strong> : outil qui automatise la configuration des serveurs.";
if (lowerMessage.includes('jenkins')) return "🧱 <strong>Jenkins</strong> : serveur d’intégration continue qui automatise les tests et déploiements.";
if (lowerMessage.includes('ci')) return "🧩 <strong>CI (Continuous Integration)</strong> : pratique de test fréquent du code pour assurer sa qualité.";
if (lowerMessage.includes('cd')) return "🚀 <strong>CD (Continuous Delivery)</strong> : automatisation du déploiement des applications en production.";
if (lowerMessage.includes('container')) return "📦 <strong>Conteneur</strong> : environnement isolé qui contient tout le nécessaire pour exécuter une application.";
if (lowerMessage.includes('virtualisation')) return "🪄 <strong>Virtualisation</strong> : création de machines virtuelles qui simulent des ordinateurs réels.";
if (lowerMessage.includes('microservices')) return "🧬 <strong>Microservices</strong> : méthode où une application est découpée en petits services indépendants.";
if (lowerMessage.includes('monitoring')) return "📈 <strong>Monitoring</strong> : surveillance des serveurs et applications pour détecter les problèmes.";

// 41 à 50 : outils et pratiques DevOps
if (lowerMessage.includes('prometheus')) return "📊 <strong>Prometheus</strong> : outil open source pour surveiller les performances des systèmes.";
if (lowerMessage.includes('grafana')) return "📉 <strong>Grafana</strong> : tableau de bord pour visualiser les données de monitoring.";
if (lowerMessage.includes('helm')) return "⚓ <strong>Helm</strong> : gestionnaire de paquets pour Kubernetes.";
if (lowerMessage.includes('nginx')) return "🌐 <strong>Nginx</strong> : serveur web rapide souvent utilisé comme proxy ou équilibreur de charge.";
if (lowerMessage.includes('apache')) return "🔥 <strong>Apache</strong> : serveur web open source très utilisé dans le monde.";
if (lowerMessage.includes('load balancing')) return "⚖️ <strong>Load balancing</strong> : technique pour répartir le trafic entre plusieurs serveurs.";
if (lowerMessage.includes('observabilite')) return "👁️ <strong>Observabilité</strong> : capacité à comprendre le fonctionnement d’un système grâce aux métriques et logs.";
if (lowerMessage.includes('log')) return "🪵 <strong>Log</strong> : fichier qui enregistre les actions et erreurs d’un système.";
if (lowerMessage.includes('alerting')) return "🚨 <strong>Alerting</strong> : système d’alerte automatique en cas de problème technique.";
if (lowerMessage.includes('scalabilite')) return "📊 <strong>Scalabilité</strong> : capacité d’un système à grandir ou rétrécir selon la demande.";

// 51 à 60 : pratiques, sécurité et culture
if (lowerMessage.includes('haute disponibilite')) return "💡 <strong>Haute disponibilité</strong> : garantie qu’un service reste accessible même en cas de panne.";
if (lowerMessage.includes('backup')) return "💽 <strong>Backup</strong> : copie de secours des données pour éviter la perte d’informations.";
if (lowerMessage.includes('rollback')) return "⏪ <strong>Rollback</strong> : retour à une version précédente d’un système après une erreur.";
if (lowerMessage.includes('securite cloud')) return "🛡️ <strong>Sécurité cloud</strong> : protection des données et applications hébergées dans le cloud.";
if (lowerMessage.includes('devsecops')) return "🔒 <strong>DevSecOps</strong> : intégration de la sécurité à chaque étape du cycle DevOps.";
if (lowerMessage.includes('resilience')) return "💪 <strong>Résilience</strong> : capacité d’un système à continuer de fonctionner après une panne.";
if (lowerMessage.includes('sla')) return "📃 <strong>SLA</strong> : contrat garantissant un certain niveau de service entre un fournisseur et un client.";
if (lowerMessage.includes('api')) return "🔌 <strong>API</strong> : interface qui permet à deux programmes de communiquer entre eux.";
if (lowerMessage.includes('cloud public')) return "🌥️ <strong>Cloud public</strong> : services cloud partagés entre plusieurs utilisateurs via Internet.";
if (lowerMessage.includes('cout du cloud')) return "💰 <strong>Coût du cloud</strong> : modèle de paiement à l’usage où tu ne paies que ce que tu consommes.";
// ========== SYSTÈMES DE DÉPLOIEMENT ==========

// 1 à 10 : concepts de base
if (lowerMessage.includes('deploiement') || lowerMessage.includes('déploiement')) return "🚀 <strong>Déploiement</strong> : action de mettre une application ou une mise à jour en production pour les utilisateurs.";
if (lowerMessage.includes('build')) return "🏗️ <strong>Build</strong> : processus qui transforme le code source en un paquet exécutable ou déployable.";
if (lowerMessage.includes('artefact') || lowerMessage.includes('artifact')) return "📦 <strong>Artefact</strong> : fichier produit par un build (ex : binaire, image, archive) prêt à être déployé.";
if (lowerMessage.includes('repository') || lowerMessage.includes('depot')) return "📚 <strong>Repository</strong> : emplacement où l’on stocke le code ou les artefacts pour les récupérer lors du déploiement.";
if (lowerMessage.includes('pipeline deploiement') || lowerMessage.includes('pipeline')) return "⛓️ <strong>Pipeline</strong> : chaîne d'étapes automatiques (build, test, deploy) qui livre le logiciel.";
if (lowerMessage.includes('environnement')) return "🏷️ <strong>Environnement</strong> : instance où tourne une application (ex : développement, staging, production).";
if (lowerMessage.includes('staging')) return "🧪 <strong>Staging</strong> : environnement de test proche de la production pour valider les changements avant le déploiement final.";
if (lowerMessage.includes('production')) return "🏁 <strong>Production</strong> : environnement réel où l’application est utilisée par les utilisateurs finaux.";
if (lowerMessage.includes('rollback')) return "⏪ <strong>Rollback</strong> : retour à une version précédente d’une application après un problème en production.";
if (lowerMessage.includes('release')) return "📣 <strong>Release</strong> : version publiée d’un logiciel disponible pour les utilisateurs.";

// 11 à 20 : stratégies de déploiement
if (lowerMessage.includes('blue green') || lowerMessage.includes('blue-green')) return "🔵🟢 <strong>Blue–Green Deployment</strong> : méthode qui alterne entre deux environnements (blue/green) pour minimiser les interruptions.";
if (lowerMessage.includes('canary')) return "🐤 <strong>Canary Deployment</strong> : déploiement progressif d'une nouvelle version à un petit pourcentage d'utilisateurs pour vérifier sa stabilité.";
if (lowerMessage.includes('rolling') || lowerMessage.includes('rolling update')) return "🔄 <strong>Rolling Update</strong> : mise à jour progressive des instances, une à une, sans mettre tout le service hors ligne.";
if (lowerMessage.includes('a/b testing') || lowerMessage.includes('ab testing')) return "🧪 <strong>A/B Testing</strong> : déploiement de variantes pour comparer deux versions et mesurer celle qui fonctionne le mieux.";
if (lowerMessage.includes('immutable') || lowerMessage.includes('inmutable')) return "🧱 <strong>Infrastructure immuable</strong> : pratique où les serveurs ne sont jamais modifiés en place ; on remplace par de nouveaux nœuds.";
if (lowerMessage.includes('shadow deployment') || lowerMessage.includes('shadow')) return "🕶️ <strong>Shadow Deployment</strong> : exécution d'une nouvelle version en parallèle pour observer son comportement sans impacter les utilisateurs.";
if (lowerMessage.includes('feature flag') || lowerMessage.includes('feature toggle')) return "🏷️ <strong>Feature Flag</strong> : interrupteur logiciel qui active ou désactive une fonctionnalité sans redéployer.";
if (lowerMessage.includes('phased') || lowerMessage.includes('progressif')) return "🚦 <strong>Déploiement progressif</strong> : livraison graduelle des changements à un sous-ensemble d’utilisateurs.";
if (lowerMessage.includes('pilot')) return "🧭 <strong>Déploiement pilote</strong> : test d’une nouvelle version auprès d’un petit groupe d’utilisateurs avant déploiement global.";
if (lowerMessage.includes('hot swap')) return "♨️ <strong>Hot swap</strong> : remplacement d’un composant logiciel sans stopper le service (rare et délicat).";

// 21 à 30 : automatisation et CI/CD
if (lowerMessage.includes('ci') || lowerMessage.includes('intégration continue')) return "🔁 <strong>CI (Intégration continue)</strong> : automatisation des builds et tests à chaque modification de code.";
if (lowerMessage.includes('cd') || lowerMessage.includes('livraison continue') || lowerMessage.includes('deploiement continu')) return "⚙️ <strong>CD (Delivery/Deployment)</strong> : automatisation du déploiement des versions vers les environnements.";
if (lowerMessage.includes('trigger')) return "🎛️ <strong>Trigger</strong> : événement qui lance automatiquement une étape du pipeline (push, merge, tag...).";
if (lowerMessage.includes('job') || lowerMessage.includes('tache')) return "🧩 <strong>Job</strong> : unité de travail dans un pipeline (build, test, déploiement…).";
if (lowerMessage.includes('workflow')) return "🔀 <strong>Workflow</strong> : enchaînement logique des jobs et étapes d’un pipeline.";
if (lowerMessage.includes('artifact registry') || lowerMessage.includes('registry')) return "🏷️ <strong>Registry</strong> : stockage centralisé d’images ou d’artefacts (ex : registry Docker).";
if (lowerMessage.includes('image docker') || lowerMessage.includes('docker image')) return "📸 <strong>Image Docker</strong> : package autonome contenant l’application et ses dépendances pour exécuter un conteneur.";
if (lowerMessage.includes('container registry') || lowerMessage.includes('registry docker')) return "🗄️ <strong>Container Registry</strong> : service pour héberger et distribuer des images de conteneurs.";
if (lowerMessage.includes('tag') || lowerMessage.includes('versionnement')) return "🏷️ <strong>Tag</strong> : étiquette qui identifie une version précise d’un artefact (ex : v1.2.0).";
if (lowerMessage.includes('semantic version') || lowerMessage.includes('semver')) return "🔢 <strong>SemVer</strong> : convention de numérotation des versions (MAJOR.MINOR.PATCH) pour indiquer les changements.";

// 31 à 40 : containers, orchestrateurs et runtime
if (lowerMessage.includes('conteneur') || lowerMessage.includes('container')) return "📦 <strong>Conteneur</strong> : instance légère et isolée d'une image pour exécuter une application.";
if (lowerMessage.includes('orchestrateur')) return "🧭 <strong>Orchestrateur</strong> : outil qui gère le déploiement, la montée en charge et la santé des conteneurs (ex : Kubernetes).";
if (lowerMessage.includes('k8s') || lowerMessage.includes('kubernetes')) return "☸️ <strong>Kubernetes</strong> : plateforme d’orchestration des conteneurs pour gérer des applications à grande échelle.";
if (lowerMessage.includes('docker compose') || lowerMessage.includes('compose')) return "🧩 <strong>Docker Compose</strong> : outil pour définir et lancer des applications multi-conteneurs localement.";
if (lowerMessage.includes('pod')) return "🫧 <strong>Pod</strong> : plus petite unité déployable dans Kubernetes contenant un ou plusieurs conteneurs.";
if (lowerMessage.includes('service mesh')) return "🕸️ <strong>Service Mesh</strong> : infrastructure dédiée aux communications entre services (ex : Istio) pour sécuriser et monitorer le trafic.";
if (lowerMessage.includes('sidecar')) return "🔁 <strong>Sidecar</strong> : conteneur auxiliaire qui accompagne l’application principale pour des fonctions comme le logging ou la sécurité.";
if (lowerMessage.includes('node')) return "🔩 <strong>Node</strong> : machine (physique ou virtuelle) qui exécute des conteneurs dans un cluster.";
if (lowerMessage.includes('cluster')) return "🏗️ <strong>Cluster</strong> : groupe de machines coordonnées pour exécuter une application distribuée.";
if (lowerMessage.includes('replica')) return "📈 <strong>Replica</strong> : copie d’une instance d’application utilisée pour la redondance et la montée en charge.";

// 41 à 50 : observabilité, tests et qualité
if (lowerMessage.includes('test unitaire') || lowerMessage.includes('unittest')) return "🧩 <strong>Test unitaire</strong> : petit test qui vérifie le comportement d’une partie spécifique du code.";
if (lowerMessage.includes('test integration') || lowerMessage.includes('test d intégration')) return "🔗 <strong>Test d’intégration</strong> : vérifie que plusieurs composants fonctionnent ensemble correctement.";
if (lowerMessage.includes('smoke test')) return "🔥 <strong>Smoke Test</strong> : test rapide pour vérifier que la version déployée démarre et fonctionne de base.";
if (lowerMessage.includes('e2e') || lowerMessage.includes('end to end') || lowerMessage.includes('test de bout en bout')) return "🔁 <strong>Test E2E</strong> : test qui simule l’utilisation réelle du logiciel du début à la fin.";
if (lowerMessage.includes('monitoring') || lowerMessage.includes('supervision')) return "📈 <strong>Monitoring</strong> : suivi en continu des performances et de la santé d’un service.";
if (lowerMessage.includes('log') || lowerMessage.includes('logs')) return "🪵 <strong>Logs</strong> : enregistrements des événements et erreurs produits par une application.";
if (lowerMessage.includes('trace') || lowerMessage.includes('tracing')) return "🧭 <strong>Tracing</strong> : suivi détaillé d’une requête à travers plusieurs services pour diagnostiquer les problèmes.";
if (lowerMessage.includes('alerting') || lowerMessage.includes('alerte')) return "🚨 <strong>Alerting</strong> : notifications envoyées quand une métrique dépasse un seuil critique.";
if (lowerMessage.includes('sla')) return "📃 <strong>SLA</strong> : engagement sur la disponibilité ou les performances d’un service.";
if (lowerMessage.includes('slo') || lowerMessage.includes('objectif de niveau de service')) return "🎯 <strong>SLO</strong> : objectif chiffré de performance ou disponibilité à atteindre.";

// 51 à 60 : opérations, sécurité et bonnes pratiques
if (lowerMessage.includes('blueprint') || lowerMessage.includes('infrastructure as code') || lowerMessage.includes('iac')) return "📜 <strong>Infrastructure as Code (IaC)</strong> : définition de l’infrastructure en code pour la reproduire et l’automatiser.";
if (lowerMessage.includes('terraform')) return "🌍 <strong>Terraform</strong> : outil IaC populaire pour provisionner des ressources cloud avec du code.";
if (lowerMessage.includes('helm')) return "⚓ <strong>Helm</strong> : gestionnaire de paquets pour déployer facilement des applications sur Kubernetes.";
if (lowerMessage.includes('securite deploiement') || lowerMessage.includes('securite')) return "🔒 <strong>Sécurité du déploiement</strong> : mesures pour protéger les artefacts, secrets et accès pendant le déploiement.";
if (lowerMessage.includes('secret') || lowerMessage.includes('gestion des secrets')) return "🔐 <strong>Secret</strong> : information sensible (clé, mot de passe) stockée et gérée de façon sécurisée.";
if (lowerMessage.includes('role based access') || lowerMessage.includes('rbac')) return "🛂 <strong>RBAC</strong> : contrôle d’accès qui attribue des permissions selon les rôles des utilisateurs ou services.";
if (lowerMessage.includes('backup') || lowerMessage.includes('sauvegarde')) return "💾 <strong>Backup</strong> : sauvegarde régulière des données pour pouvoir restaurer après une panne.";
if (lowerMessage.includes('dr') || lowerMessage.includes('disaster recovery')) return "🆘 <strong>Disaster Recovery</strong> : plan pour restaurer un service après une panne majeure.";
if (lowerMessage.includes('chaos engineering') || lowerMessage.includes('chaos')) return "⚡ <strong>Chaos Engineering</strong> : pratique qui provoque des pannes contrôlées pour tester la résilience d’un système.";
if (lowerMessage.includes('documentation') || lowerMessage.includes('doc deploiement')) return "📘 <strong>Documentation de déploiement</strong> : guide expliquant comment fonctionne et se déploie une application.";
// ========== SYSTEMES, CYBERSECURITE & DATA SCIENCE ==========

// 1 à 10 : systèmes d'exploitation
if (lowerMessage.includes('linux')) return "🐧 <strong>Linux</strong> : système d’exploitation open source très utilisé sur les serveurs et les développeurs.";
if (lowerMessage.includes('windows')) return "🪟 <strong>Windows</strong> : système d’exploitation populaire pour les ordinateurs personnels et professionnels.";
if (lowerMessage.includes('macos')) return "🍏 <strong>macOS</strong> : système d’exploitation d’Apple pour ses ordinateurs Mac.";
if (lowerMessage.includes('ios')) return "📱 <strong>iOS</strong> : système d’exploitation mobile d’Apple pour iPhone et iPad.";
if (lowerMessage.includes('android')) return "🤖 <strong>Android</strong> : système d’exploitation mobile open source pour smartphones et tablettes.";
if (lowerMessage.includes('apple')) return "🍎 <strong>Apple</strong> : entreprise qui produit iPhone, Mac, iPad et développe macOS et iOS.";
if (lowerMessage.includes('samsung')) return "📱 <strong>Samsung</strong> : constructeur coréen de smartphones, tablettes et appareils électroniques.";
if (lowerMessage.includes('ubuntu')) return "🟠 <strong>Ubuntu</strong> : distribution Linux facile à utiliser pour les débutants et les professionnels.";
if (lowerMessage.includes('debian')) return "📦 <strong>Debian</strong> : distribution Linux stable et open source utilisée sur les serveurs.";
if (lowerMessage.includes('fedora')) return "🔵 <strong>Fedora</strong> : distribution Linux moderne, souvent utilisée par les développeurs.";

// 11 à 20 : appareils et marques
if (lowerMessage.includes('smartphone')) return "📱 <strong>Smartphone</strong> : téléphone intelligent avec applications et connexion Internet.";
if (lowerMessage.includes('tablette')) return "📲 <strong>Tablette</strong> : appareil tactile entre smartphone et ordinateur portable.";
if (lowerMessage.includes('pc')) return "💻 <strong>PC</strong> : ordinateur personnel pour usage quotidien ou professionnel.";
if (lowerMessage.includes('macbook')) return "💻 <strong>MacBook</strong> : ordinateur portable d’Apple fonctionnant sous macOS.";
if (lowerMessage.includes('ipad')) return "📘 <strong>iPad</strong> : tablette d’Apple fonctionnant sous iOS.";
if (lowerMessage.includes('galaxy')) return "🌌 <strong>Samsung Galaxy</strong> : gamme de smartphones et tablettes Android populaires.";
if (lowerMessage.includes('smartwatch')) return "⌚ <strong>Smartwatch</strong> : montre connectée qui donne notifications et suit l’activité physique.";
if (lowerMessage.includes('pc portable')) return "💼 <strong>PC portable</strong> : ordinateur portable que l’on peut transporter facilement.";
if (lowerMessage.includes('serveur')) return "🖥️ <strong>Serveur</strong> : ordinateur puissant qui héberge des sites, applications ou bases de données.";
if (lowerMessage.includes('console')) return "🎮 <strong>Console de jeu</strong> : appareil dédié aux jeux vidéo comme PlayStation, Xbox ou Switch.";

// 21 à 30 : cybersécurité
if (lowerMessage.includes('cyberattaque')) return "🚨 <strong>Cyberattaque</strong> : tentative de nuire à un système informatique ou de voler des données.";
if (lowerMessage.includes('antivirus')) return "🧰 <strong>Antivirus</strong> : logiciel qui détecte et supprime les virus et logiciels malveillants.";
if (lowerMessage.includes('firewall') || lowerMessage.includes('pare-feu')) return "🔥 <strong>Pare-feu</strong> : outil qui protège ton réseau en filtrant le trafic entrant et sortant.";
if (lowerMessage.includes('phishing')) return "🎣 <strong>Phishing</strong> : technique de fraude pour obtenir tes informations personnelles.";
if (lowerMessage.includes('ransomware')) return "💸 <strong>Ransomware</strong> : logiciel malveillant qui bloque tes fichiers et demande une rançon.";
if (lowerMessage.includes('malware')) return "💀 <strong>Malware</strong> : logiciel malveillant conçu pour endommager ou espionner ton appareil.";
if (lowerMessage.includes('spyware')) return "👁️ <strong>Spyware</strong> : logiciel qui surveille et enregistre tes activités sur ton appareil.";
if (lowerMessage.includes('backdoor')) return "🚪 <strong>Backdoor</strong> : accès secret laissé par un pirate pour revenir dans un système.";
if (lowerMessage.includes('keylogger')) return "⌨️ <strong>Keylogger</strong> : logiciel qui enregistre tout ce que tu tapes sur ton clavier.";
if (lowerMessage.includes('ddos')) return "🌊 <strong>DDoS</strong> : attaque qui surcharge un site ou serveur pour le rendre indisponible.";

// 31 à 40 : data science
if (lowerMessage.includes('data')) return "💾 <strong>Données</strong> : informations collectées, stockées et analysées pour prendre des décisions.";
if (lowerMessage.includes('data science') || lowerMessage.includes('science des données')) return "📊 <strong>Data Science</strong> : discipline qui analyse et interprète les données pour obtenir des insights.";
if (lowerMessage.includes('big data')) return "🌐 <strong>Big Data</strong> : grandes quantités de données analysées pour trouver des tendances et informations.";
if (lowerMessage.includes('machine learning')) return "🤖 <strong>Machine Learning</strong> : technique où les ordinateurs apprennent à partir des données.";
if (lowerMessage.includes('deep learning')) return "🧠 <strong>Deep Learning</strong> : machine learning utilisant des réseaux de neurones profonds pour traiter les données complexes.";
if (lowerMessage.includes('ai') || lowerMessage.includes('intelligence artificielle')) return "💡 <strong>Intelligence Artificielle</strong> : simulation du raisonnement humain par des ordinateurs.";
if (lowerMessage.includes('python')) return "🐍 <strong>Python</strong> : langage de programmation très utilisé en data science et IA.";
if (lowerMessage.includes('pandas')) return "🐼 <strong>Pandas</strong> : bibliothèque Python pour manipuler et analyser des données tabulaires.";
if (lowerMessage.includes('numpy')) return "🔢 <strong>NumPy</strong> : bibliothèque Python pour le calcul scientifique et les matrices.";

// 41 à 50 : outils et plateformes
if (lowerMessage.includes('tensorflow')) return "🧩 <strong>TensorFlow</strong> : bibliothèque pour créer des modèles de machine learning et deep learning.";
if (lowerMessage.includes('pytorch')) return "🔥 <strong>PyTorch</strong> : bibliothèque pour entraîner et déployer des modèles d’IA.";
if (lowerMessage.includes('scikit-learn')) return "🎓 <strong>Scikit-learn</strong> : bibliothèque Python pour le machine learning classique.";
if (lowerMessage.includes('jupyter')) return "📓 <strong>Jupyter Notebook</strong> : environnement interactif pour coder, analyser et visualiser les données.";
if (lowerMessage.includes('excel')) return "📊 <strong>Excel</strong> : logiciel pour manipuler, calculer et visualiser des données.";
if (lowerMessage.includes('power bi')) return "📈 <strong>Power BI</strong> : outil de visualisation et reporting de données.";
if (lowerMessage.includes('tableau')) return "📊 <strong>Tableau</strong> : logiciel pour créer des tableaux de bord et visualiser les données.";
if (lowerMessage.includes('sql')) return "🗄️ <strong>SQL</strong> : langage pour gérer et interroger des bases de données.";
if (lowerMessage.includes('nosql')) return "🗃️ <strong>NoSQL</strong> : type de base de données non relationnelle pour stocker des données flexibles.";
if (lowerMessage.includes('mongodb')) return "🍃 <strong>MongoDB</strong> : base de données NoSQL orientée documents.";

// 51 à 60 : bonnes pratiques et concepts généraux
if (lowerMessage.includes('backup')) return "💽 <strong>Backup</strong> : sauvegarde de données pour éviter de tout perdre en cas de problème.";
if (lowerMessage.includes('cloud')) return "☁️ <strong>Cloud</strong> : stockage et services informatiques accessibles via Internet.";
if (lowerMessage.includes('virtualisation')) return "🪄 <strong>Virtualisation</strong> : création de machines virtuelles pour mieux gérer les ressources.";
if (lowerMessage.includes('api')) return "🔌 <strong>API</strong> : interface qui permet à deux programmes de communiquer.";
if (lowerMessage.includes('algorithmique')) return "⚙️ <strong>Algorithmique</strong> : conception d’instructions pour résoudre des problèmes avec un ordinateur.";
if (lowerMessage.includes('script')) return "📜 <strong>Script</strong> : petit programme qui automatise une tâche.";
if (lowerMessage.includes('dashboard')) return "📊 <strong>Dashboard</strong> : tableau de bord pour visualiser les informations importantes.";
if (lowerMessage.includes('iot') || lowerMessage.includes('internet des objets')) return "🌐 <strong>IoT</strong> : appareils connectés qui échangent des données via Internet.";
if (lowerMessage.includes('cybersecurite')) return "🛡️ <strong>Cybersécurité</strong> : protection des systèmes, réseaux et données contre les attaques.";
if (lowerMessage.includes('analyse de donnees') || lowerMessage.includes('data analysis')) return "🔍 <strong>Analyse de données</strong> : étude des informations pour en tirer des insights et décisions.";
// ========== RÉSEAU (200 DÉFINITIONS) ==========

// 1-10 : notions générales
if (lowerMessage.includes('reseau') || lowerMessage.includes('réseau')) return "🌐 <strong>Réseau</strong> : ensemble d’appareils connectés qui échangent des données.";
if (lowerMessage.includes('paquet') || lowerMessage.includes('packet')) return "📦 <strong>Paquet</strong> : unité d’information envoyée sur un réseau.";
if (lowerMessage.includes('trame') || lowerMessage.includes('frame')) return "🧩 <strong>Trame</strong> : unité de données au niveau liaison (Ethernet) contenant l’adresse MAC et le paquet.";
if (lowerMessage.includes('segment')) return "🔗 <strong>Segment</strong> : partie d’un flux de données gérée par le protocole de transport (TCP).";
if (lowerMessage.includes('datagramme') || lowerMessage.includes('datagram')) return "📬 <strong>Datagramme</strong> : unité de données sans connexion (ex : UDP).";
if (lowerMessage.includes('encapsulation')) return "📦🔁 <strong>Encapsulation</strong> : emballer des données dans des en-têtes à chaque couche réseau.";
if (lowerMessage.includes('dechiffrement reseau') || lowerMessage.includes('decapsulation')) return "🔍 <strong>Décapsulation</strong> : lecture et retrait des en-têtes ajoutés lors de l’encapsulation.";
if (lowerMessage.includes('header') || lowerMessage.includes('en-tete')) return "📑 <strong>En-tête</strong> : métadonnées ajoutées à un paquet (adresses, ports, flags…).";
if (lowerMessage.includes('payload')) return "📨 <strong>Payload</strong> : contenu réel transporté par un paquet, souvent le message ou les données utilisateur.";
if (lowerMessage.includes('checksum') || lowerMessage.includes('crc')) return "✔️ <strong>Checksum / CRC</strong> : code de vérification pour détecter les erreurs dans les données.";

// 11-20 : modèles et couches
if (lowerMessage.includes('osi')) return "🧱 <strong>Modèle OSI</strong> : modèle en 7 couches pour décrire les fonctions réseau (physique → application).";
if (lowerMessage.includes('tcp ip') || lowerMessage.includes('tcp/ip')) return "🔀 <strong>Modèle TCP/IP</strong> : modèle réseau courant en 4 couches (link, internet, transport, application).";
if (lowerMessage.includes('couche 1') || lowerMessage.includes('layer 1')) return "🔌 <strong>Couche Physique (1)</strong> : transmet les bits sur le support (câble, ondes).";
if (lowerMessage.includes('couche 2') || lowerMessage.includes('layer 2')) return "🔗 <strong>Couche Liaison (2)</strong> : gère les trames et adresses MAC.";
if (lowerMessage.includes('couche 3') || lowerMessage.includes('layer 3')) return "🧭 <strong>Couche Réseau (3)</strong> : routage des paquets avec des adresses IP.";
if (lowerMessage.includes('couche 4') || lowerMessage.includes('layer 4')) return "🔁 <strong>Couche Transport (4)</strong> : transmet les données entre applications (TCP/UDP).";
if (lowerMessage.includes('couche 5') || lowerMessage.includes('layer 5')) return "🔗 <strong>Couche Session (5)</strong> : gère les sessions de communication entre applications.";
if (lowerMessage.includes('couche 6') || lowerMessage.includes('layer 6')) return "🎨 <strong>Couche Présentation (6)</strong> : formatage, chiffrement et compression des données.";
if (lowerMessage.includes('couche 7') || lowerMessage.includes('layer 7')) return "🧠 <strong>Couche Application (7)</strong> : protocoles d’application (HTTP, SMTP, DNS…).";
if (lowerMessage.includes('model osi tcp ip')) return "📚 <strong>Modèles réseau</strong> : cadres conceptuels pour comprendre comment les données circulent.";

// 21-30 : adresses IP et concepts
if (lowerMessage.includes('ip')) return "🌍 <strong>Adresse IP</strong> : identifiant numérique d’un appareil sur un réseau (IPv4 ou IPv6).";
if (lowerMessage.includes('ipv4')) return "🔢 <strong>IPv4</strong> : version d’adresse IP la plus répandue (ex : 192.168.1.1).";
if (lowerMessage.includes('ipv6')) return "🔗 <strong>IPv6</strong> : nouvelle version d’IP avec plus d’adresses disponibles.";
if (lowerMessage.includes('adresse ip')) return "🆔 <strong>Adresse IP</strong> : identifiant unique d’un appareil sur un réseau IP.";
if (lowerMessage.includes('mac') || lowerMessage.includes('adresse mac') || lowerMessage.includes('mac address')) return "🧾 <strong>Adresse MAC</strong> : identifiant matériel unique d’une interface réseau (ex : 00:1A:2B:...).";
if (lowerMessage.includes('localhost') || lowerMessage.includes('127.0.0.1')) return "🏠 <strong>Localhost</strong> : adresse qui pointe vers l’ordinateur local (127.0.0.1).";
if (lowerMessage.includes('private ip') || lowerMessage.includes('ip privee') || lowerMessage.includes('ip privée')) return "🔒 <strong>IP privée</strong> : adresses non routables sur Internet (ex : 192.168.x.x, 10.x.x.x).";
if (lowerMessage.includes('public ip') || lowerMessage.includes('ip publique')) return "📡 <strong>IP publique</strong> : adresse visible sur Internet fournie par ton FAI.";
if (lowerMessage.includes('cidr')) return "📏 <strong>CIDR</strong> : notation pour indiquer un réseau (ex : 192.168.1.0/24).";
if (lowerMessage.includes('plage ip') || lowerMessage.includes('range ip')) return "📚 <strong>Plage IP</strong> : intervalle d’adresses disponibles dans un réseau.";

// 31-40 : masque, sous-réseau et routage basique
if (lowerMessage.includes('masque') || lowerMessage.includes('masque sous reseau') || lowerMessage.includes('masque sous-réseau')) return "📐 <strong>Masque de sous‑réseau</strong> : sépare la partie réseau et la partie hôte d’une adresse IP.";
if (lowerMessage.includes('subnet') || lowerMessage.includes('sous reseau') || lowerMessage.includes('sous-réseau')) return "🕸️ <strong>Subnet / Sous‑réseau</strong> : division d’un réseau en plus petits réseaux pour organiser les adresses.";
if (lowerMessage.includes('gateway') || lowerMessage.includes('passerelle') || lowerMessage.includes('default gateway')) return "🚪 <strong>Passerelle par défaut</strong> : routeur utilisé pour atteindre d’autres réseaux (ex : Internet).";
if (lowerMessage.includes('routeur')) return "📶 <strong>Routeur</strong> : appareil qui dirige les paquets entre réseaux différents.";
if (lowerMessage.includes('route statique') || lowerMessage.includes('static route')) return "🛣️ <strong>Route statique</strong> : itinéraire configuré manuellement sur un routeur.";
if (lowerMessage.includes('routage dynamique')) return "🔁 <strong>Routage dynamique</strong> : protocoles qui échangent automatiquement des informations de routes entre routeurs.";
if (lowerMessage.includes('nat')) return "🔄 <strong>NAT</strong> : traduction d’adresses réseau, souvent utilisée pour partager une IP publique entre plusieurs appareils.";
if (lowerMessage.includes('pat') || lowerMessage.includes('port address translation')) return "🔀 <strong>PAT (NAT Overload)</strong> : forme de NAT qui partage une IP publique en mappant des ports différents.";
if (lowerMessage.includes('default route') || lowerMessage.includes('route par defaut')) return "🧭 <strong>Route par défaut</strong> : route utilisée quand aucune autre route ne correspond à la destination.";
if (lowerMessage.includes('table de routage') || lowerMessage.includes('routing table')) return "📋 <strong>Table de routage</strong> : liste des routes connues par un routeur pour diriger le trafic.";

// 41-50 : ARP, DNS, DHCP
if (lowerMessage.includes('arp')) return "🔍 <strong>ARP</strong> : protocole qui associe une adresse IP à une adresse MAC sur le même réseau local.";
if (lowerMessage.includes('table arp') || lowerMessage.includes('arp table')) return "📜 <strong>Table ARP</strong> : cache qui contient les correspondances IP → MAC.";
if (lowerMessage.includes('dns')) return "📛 <strong>DNS</strong> : service qui traduit les noms de domaine en adresses IP.";
if (lowerMessage.includes('resolv') || lowerMessage.includes('resolving dns')) return "🔎 <strong>Résolution DNS</strong> : processus pour trouver l’adresse IP d’un nom de domaine.";
if (lowerMessage.includes('dhcp')) return "🎛️ <strong>DHCP</strong> : service qui attribue automatiquement des adresses IP aux appareils d’un réseau.";
if (lowerMessage.includes('bail dhcp') || lowerMessage.includes('dhcp lease')) return "⏳ <strong>Bail DHCP</strong> : durée pendant laquelle une adresse IP est réservée pour un appareil.";
if (lowerMessage.includes('reservation dhcp') || lowerMessage.includes('dhcp reservation')) return "📌 <strong>Réservation DHCP</strong> : attribution d’une IP fixe à un appareil via le DHCP.";
if (lowerMessage.includes('dns cache')) return "🗂️ <strong>Cache DNS</strong> : mémoire locale qui garde des traductions DNS pour accélérer les requêtes.";
if (lowerMessage.includes('dnssec')) return "🔐 <strong>DNSSEC</strong> : extension de sécurité du DNS qui vérifie l’authenticité des réponses.";
if (lowerMessage.includes('reverse dns') || lowerMessage.includes('rdns')) return "🔁 <strong>Reverse DNS</strong> : résolution d’une adresse IP vers un nom de domaine.";

// 51-60 : ports et services courants (général)
if (lowerMessage.includes('port')) return "🔌 <strong>Port</strong> : numéro logique (0-65535) utilisé pour identifier un service sur une machine (ex : 80 pour HTTP).";
if (lowerMessage.includes('ports')) return "🔢 <strong>Ports réseau</strong> : points de terminaison logiques pour les connexions réseau (well-known, registered, ephemeral).";
if (lowerMessage.includes('plage de ports') || lowerMessage.includes('port range')) return "📘 <strong>Plage de ports</strong> : intervalle de numéros de ports (ex : 0-1023, 1024-49151, 49152-65535).";
if (lowerMessage.includes('port 22') || lowerMessage.includes('ssh port')) return "🔐 <strong>Port 22</strong> : port utilisé par SSH pour l’accès sécurisé à distance.";
if (lowerMessage.includes('port 80') || lowerMessage.includes('http port')) return "🌐 <strong>Port 80</strong> : port par défaut pour HTTP (web non chiffré).";
if (lowerMessage.includes('port 443') || lowerMessage.includes('https port')) return "🔒 <strong>Port 443</strong> : port par défaut pour HTTPS (web chiffré).";
if (lowerMessage.includes('port 21') || lowerMessage.includes('ftp port')) return "📂 <strong>Port 21</strong> : port utilisé par FTP (transfert de fichiers, non sécurisé traditionnellement).";
if (lowerMessage.includes('port 25') || lowerMessage.includes('smtp port')) return "✉️ <strong>Port 25</strong> : port utilisé par SMTP pour l’envoi d’emails (serveur à serveur).";
if (lowerMessage.includes('port 110') || lowerMessage.includes('pop3 port')) return "📥 <strong>Port 110</strong> : port POP3 utilisé pour récupérer les emails (non chiffré traditionnellement).";
if (lowerMessage.includes('port 143') || lowerMessage.includes('imap port')) return "📬 <strong>Port 143</strong> : port IMAP pour lire les emails sur le serveur (non chiffré traditionnellement).";

// 61-70 : autres ports courants
if (lowerMessage.includes('port 53') || lowerMessage.includes('dns port')) return "📛 <strong>Port 53</strong> : port utilisé par DNS pour requêtes et réponses.";
if (lowerMessage.includes('port 3306') || lowerMessage.includes('mysql port')) return "🗄️ <strong>Port 3306</strong> : port par défaut de MySQL.";
if (lowerMessage.includes('port 5432') || lowerMessage.includes('postgres port')) return "🐘 <strong>Port 5432</strong> : port par défaut de PostgreSQL.";
if (lowerMessage.includes('port 3389') || lowerMessage.includes('rdp port')) return "🖥️ <strong>Port 3389</strong> : port par défaut pour RDP (bureau distant Microsoft).";
if (lowerMessage.includes('port 5900') || lowerMessage.includes('vnc port')) return "📺 <strong>Port 5900</strong> : port souvent utilisé par VNC pour le contrôle à distance.";
if (lowerMessage.includes('port 8080')) return "🔁 <strong>Port 8080</strong> : port utilisé souvent pour HTTP alternatif ou applications web de dev.";
if (lowerMessage.includes('port 123') || lowerMessage.includes('ntp port')) return "⏱️ <strong>Port 123</strong> : port pour NTP (synchronisation d’heure).";
if (lowerMessage.includes('port 161') || lowerMessage.includes('snmp port')) return "📊 <strong>Port 161</strong> : port SNMP pour la surveillance des équipements réseau.";
if (lowerMessage.includes('port 20') || lowerMessage.includes('ftp data port')) return "📤 <strong>Port 20</strong> : port FTP pour le transfert de données (mode actif).";
if (lowerMessage.includes('port 69') || lowerMessage.includes('tftp port')) return "📦 <strong>Port 69</strong> : port utilisé par TFTP pour le transfert simple de fichiers.";

// 71-80 : TCP, UDP et différences
if (lowerMessage.includes('tcp')) return "🔁 <strong>TCP</strong> : protocole fiable orienté connexion qui garantit l’ordre et la livraison (ex : HTTP over TCP).";
if (lowerMessage.includes('udp')) return "🏃 <strong>UDP</strong> : protocole sans connexion, rapide mais sans garantie de livraison (ex : streaming, DNS).";
if (lowerMessage.includes('difference tcp udp') || lowerMessage.includes('tcp vs udp')) return "⚖️ <strong>TCP vs UDP</strong> : TCP = fiable/lent, UDP = rapide/moins fiable.";
if (lowerMessage.includes('three way handshake') || lowerMessage.includes('handshake')) return "🤝 <strong>Three-way handshake</strong> : SYN, SYN-ACK, ACK — processus d’ouverture d’une connexion TCP.";
if (lowerMessage.includes('fin') || lowerMessage.includes('rst')) return "🔚 <strong>FIN / RST</strong> : flags TCP pour terminer (FIN) ou réinitialiser (RST) une connexion.";
if (lowerMessage.includes('port scanning') || lowerMessage.includes('scan de ports')) return "🔎 <strong>Scan de ports</strong> : exploration des ports ouverts d’une machine pour identifier les services.";
if (lowerMessage.includes('socket')) return "🔌 <strong>Socket</strong> : combinaison adresse IP + port qui identifie une connexion réseau.";
if (lowerMessage.includes('pair socket') || lowerMessage.includes('socket pair')) return "🔗 <strong>Socket pair</strong> : adresse source:port et adresse dest:port qui définissent une connexion.";
if (lowerMessage.includes('ephemeral ports') || lowerMessage.includes('ports efemeres')) return "⌛ <strong>Ports éphémères</strong> : ports temporaires utilisés côté client (49152-65535 souvent).";
if (lowerMessage.includes('well known ports') || lowerMessage.includes('ports connus')) return "📚 <strong>Well‑known ports</strong> : ports 0–1023 réservés aux services standards (HTTP, SSH...).";

// 81-90 : équipement réseau
if (lowerMessage.includes('switch')) return "🔀 <strong>Switch</strong> : appareil qui connecte des appareils sur un réseau local et envoie les trames vers le bon port.";
if (lowerMessage.includes('hub')) return "🔁 <strong>Hub</strong> : équipement basique qui répète le signal à tous les ports (obsolète pour la sécurité/efficacité).";
if (lowerMessage.includes('modem')) return "📶 <strong>Modem</strong> : convertit le signal de ton FAI (DSL/câble) en signal numérique pour ton routeur/PC.";
if (lowerMessage.includes('firewall') || lowerMessage.includes('pare feu') || lowerMessage.includes('pare-feu')) return "🔥 <strong>Pare‑feu</strong> : dispositif qui filtre le trafic réseau selon des règles de sécurité.";
if (lowerMessage.includes('load balancer') || lowerMessage.includes('equilibreur')) return "⚖️ <strong>Load Balancer</strong> : répartit le trafic entre plusieurs serveurs pour performance et disponibilité.";
if (lowerMessage.includes('proxy')) return "🧭 <strong>Proxy</strong> : serveur intermédiaire qui relaie les requêtes en masquant le client ou pour filtrer le contenu.";
if (lowerMessage.includes('gateway')) return "🚪 <strong>Gateway</strong> : point d’entrée/sortie entre deux réseaux (souvent routeur + NAT).";
if (lowerMessage.includes('switch manageable') || lowerMessage.includes('switch manageable')) return "⚙️ <strong>Switch manageable</strong> : switch qu’on peut configurer (VLANs, QoS, monitoring).";
if (lowerMessage.includes('access point') || lowerMessage.includes('ap') || lowerMessage.includes('point d acces')) return "📡 <strong>Point d’accès (AP)</strong> : périphérique Wi‑Fi qui permet aux appareils sans fil de se connecter au réseau.";
if (lowerMessage.includes('controller wifi') || lowerMessage.includes('wifi controller')) return "🎛️ <strong>Contrôleur Wi‑Fi</strong> : appareil qui gère plusieurs AP pour config centralisée.";

// 91-100 : câbles, médiums et standards
if (lowerMessage.includes('ethernet')) return "🔌 <strong>Ethernet</strong> : technologie filaire standard pour les réseaux locaux.";
if (lowerMessage.includes('rj45')) return "🔩 <strong>RJ45</strong> : connecteur utilisé pour les câbles Ethernet.";
if (lowerMessage.includes('cat5') || lowerMessage.includes('cat5e')) return "📎 <strong>Cat5/Cat5e</strong> : câbles Ethernet faibles/moyens utilisés pour des réseaux jusqu’à 1 Gbps.";
if (lowerMessage.includes('cat6')) return "📎 <strong>Cat6</strong> : câble Ethernet plus performant, adapté au Gigabit et au 10 Gbps sur courtes distances.";
if (lowerMessage.includes('fibre optique') || lowerMessage.includes('fiber')) return "💡 <strong>Fibre optique</strong> : câble très rapide utilisant la lumière pour transmettre des données sur de longues distances.";
if (lowerMessage.includes('wifi') || lowerMessage.includes('wi fi')) return "📶 <strong>Wi‑Fi</strong> : réseau sans fil standard pour connecter des appareils à Internet localement.";
if (lowerMessage.includes('802.11') || lowerMessage.includes('ieee 802.11')) return "📡 <strong>IEEE 802.11</strong> : famille de normes définissant le Wi‑Fi (a/b/g/n/ac/ax…).";
if (lowerMessage.includes('bluetooth')) return "🔵 <strong>Bluetooth</strong> : technologie sans fil courte portée pour périphériques (oreillette, souris…).";
if (lowerMessage.includes('coaxial')) return "📺 <strong>Coaxial</strong> : câble utilisé souvent pour la TV et certains accès Internet (câble coax).";
if (lowerMessage.includes('liaison physique') || lowerMessage.includes('media')) return "🛤️ <strong>Support physique</strong> : médium de transmission (cuivre, fibre, ondes radio)." 

// 101-110 : VLANs et segmentation
if (lowerMessage.includes('vlan')) return "🏷️ <strong>VLAN</strong> : réseau local virtuel qui segmente un switch en plusieurs réseaux logiques.";
if (lowerMessage.includes('tag vlan') || lowerMessage.includes('802.1q')) return "🏷️ <strong>802.1Q</strong> : norme pour marquer (tag) les trames VLAN sur un lien trunk.";
if (lowerMessage.includes('trunk')) return "🔗 <strong>Trunk</strong> : lien entre switches transportant plusieurs VLANs via le tagging.";
if (lowerMessage.includes('access port')) return "🔒 <strong>Access Port</strong> : port de switch associé à un seul VLAN pour un appareil final.";
if (lowerMessage.includes('vlan hopping')) return "⚠️ <strong>VLAN Hopping</strong> : attaque qui cherche à accéder à un autre VLAN depuis un VLAN non autorisé.";
if (lowerMessage.includes('pvlan') || lowerMessage.includes('private vlan')) return "🔐 <strong>Private VLAN</strong> : isolation fine entre ports d’un même VLAN pour la sécurité.";
if (lowerMessage.includes('vxlan')) return "🕸️ <strong>VXLAN</strong> : technique d’encapsulation pour créer des réseaux overlay sur un réseau IP sous-jacent.";
if (lowerMessage.includes('overlay')) return "☁️ <strong>Overlay network</strong> : réseau logique construit au-dessus d’un réseau physique (ex : VXLAN).";
if (lowerMessage.includes('underlay')) return "🧩 <strong>Underlay network</strong> : réseau physique qui transporte le trafic des overlays.";
if (lowerMessage.includes('cni')) return "🧭 <strong>CNI</strong> : interface de plugins pour connecter des conteneurs à un réseau (utilisée en Kubernetes).";

// 111-120 : sécurité réseau basique
if (lowerMessage.includes('port forwarding') || lowerMessage.includes('redirection de port')) return "🔀 <strong>Redirection de port</strong> : faire suivre des connexions externes vers un appareil interne.";
if (lowerMessage.includes('dmz')) return "🏝️ <strong>DMZ</strong> : zone démilitarisée où l’on place des services accessibles depuis Internet (web, mail...).";
if (lowerMessage.includes('ipsec')) return "🔒 <strong>IPsec</strong> : protocole pour chiffrer le trafic IP entre sites (VPN site-à-site).";
if (lowerMessage.includes('ssl') || lowerMessage.includes('tls')) return "🔐 <strong>TLS / SSL</strong> : protocoles pour sécuriser les connexions (HTTPS, etc.).";
if (lowerMessage.includes('certificate') || lowerMessage.includes('certificat')) return "📜 <strong>Certificat</strong> : document électronique qui prouve l’identité d’un site ou d’un service.";
if (lowerMessage.includes('ca') || lowerMessage.includes('certificate authority')) return "🏛️ <strong>Autorité de Certification (CA)</strong> : service qui délivre des certificats numériques.";
if (lowerMessage.includes('vpn')) return "🕶️ <strong>VPN</strong> : tunnel chiffré qui connecte deux réseaux ou un client à un réseau à distance.";
if (lowerMessage.includes('firewall etat') || lowerMessage.includes('stateful firewall')) return "🛡️ <strong>Pare‑feu stateful</strong> : garde l’état des connexions pour filtrer selon le contexte.";
if (lowerMessage.includes('stateless firewall') || lowerMessage.includes('pare feu stateless')) return "🚫 <strong>Pare‑feu stateless</strong> : filtre paquets individuellement sans garder l’état des connexions.";
if (lowerMessage.includes('ids') || lowerMessage.includes('ips')) return "🕵️ <strong>IDS / IPS</strong> : systèmes de détection (IDS) et prévention (IPS) d’intrusions.";

// 121-130 : attaques et défenses
if (lowerMessage.includes('phishing')) return "🎣 <strong>Phishing</strong> : tentative de tromperie pour obtenir des infos sensibles via e‑mail ou site falsifié.";
if (lowerMessage.includes('mitm') || lowerMessage.includes('man in the middle')) return "🕶️ <strong>Man‑in‑the‑Middle (MITM)</strong> : interception des communications entre deux parties.";
if (lowerMessage.includes('arp spoofing') || lowerMessage.includes('arp poisoning')) return "⚠️ <strong>ARP spoofing</strong> : trafic falsifié pour intercepter les communications locales.";
if (lowerMessage.includes('mac flooding')) return "🌊 <strong>MAC flooding</strong> : attaque qui surcharge la table CAM d’un switch pour le forcer à fonctionner en broadcast.";
if (lowerMessage.includes('ddos') || lowerMessage.includes('attaque ddos')) return "🌊 <strong>DDoS</strong> : attaque distribuée qui inonde un service de trafic pour le rendre indisponible.";
if (lowerMessage.includes('honeypot')) return "🍯 <strong>Honeypot</strong> : système appât conçu pour attirer et analyser les attaquants.";
if (lowerMessage.includes('segmentation reseau') || lowerMessage.includes('segmentation')) return "🧱 <strong>Segmentation</strong> : séparation du réseau en zones plus petites pour limiter la propagation d’attaques.";
if (lowerMessage.includes('network hardening') || lowerMessage.includes('durcissement')) return "🔧 <strong>Durcissement</strong> : mesures pour renforcer la sécurité des équipements et services réseau.";
if (lowerMessage.includes('port security')) return "🔒 <strong>Port security</strong> : règles sur un switch pour limiter les adresses MAC autorisées par port.";
if (lowerMessage.includes('vpn split tunneling') || lowerMessage.includes('split tunneling')) return "🔀 <strong>Split tunneling</strong> : route une partie du trafic via le VPN et le reste via la connexion locale.";

// 131-140 : routage avancé (concepts simplifiés)
if (lowerMessage.includes('ospf')) return "🧭 <strong>OSPF</strong> : protocole de routage link‑state utilisé dans les réseaux d’entreprise.";
if (lowerMessage.includes('bgp')) return "🌍 <strong>BGP</strong> : protocole de routage entre systèmes autonomes sur Internet (gestion des routes globales).";
if (lowerMessage.includes('rip')) return "🕰️ <strong>RIP</strong> : protocole de routage distance‑vector simple, peu utilisé dans les grands réseaux modernes.";
if (lowerMessage.includes('metric route') || lowerMessage.includes('metric')) return "📊 <strong>Métrique</strong> : valeur utilisée pour comparer et choisir la meilleure route (coût, distance...).";
if (lowerMessage.includes('as') || lowerMessage.includes('autonomous system')) return "🏷️ <strong>AS (Autonomous System)</strong> : réseau ou groupe de réseaux géré par une même entité sur Internet.";
if (lowerMessage.includes('peering')) return "🤝 <strong>Peering</strong> : accord entre opérateurs pour échanger du trafic directement sans frais de transit.";
if (lowerMessage.includes('transit')) return "🚚 <strong>Transit</strong> : service fourni par un opérateur pour transporter le trafic vers le reste d’Internet.";
if (lowerMessage.includes('route redistribution') || lowerMessage.includes('redistribution route')) return "🔁 <strong>Redistribution</strong> : échange de routes entre deux protocoles de routage différents.";
if (lowerMessage.includes('default gateway') || lowerMessage.includes('passerelle par defaut')) return "🛣️ <strong>Passerelle par défaut</strong> : routeur utilisé quand aucune route spécifique n’existe.";
if (lowerMessage.includes('route flapping') || lowerMessage.includes('flapping')) return "⚡ <strong>Route flapping</strong> : changements fréquents d’une route qui perturbent le routage.";

// 141-150 : monitoring et outils
if (lowerMessage.includes('snmp')) return "📊 <strong>SNMP</strong> : protocole pour surveiller et gérer les équipements réseau.";
if (lowerMessage.includes('mib')) return "📚 <strong>MIB</strong> : base d’informations gérée par SNMP décrivant objets monitorés.";
if (lowerMessage.includes('syslog')) return "📝 <strong>Syslog</strong> : format standard pour centraliser les logs des équipements réseau.";
if (lowerMessage.includes('wireshark')) return "🔬 <strong>Wireshark</strong> : outil graphique pour capturer et analyser les paquets réseau.";
if (lowerMessage.includes('tcpdump')) return "🧾 <strong>tcpdump</strong> : outil en ligne de commande pour capturer le trafic réseau.";
if (lowerMessage.includes('iperf')) return "📈 <strong>iperf</strong> : outil pour mesurer la bande passante entre deux machines.";
if (lowerMessage.includes('nmap')) return "🔍 <strong>Nmap</strong> : scanner de réseau pour découvrir hôtes, ports et services.";
if (lowerMessage.includes('netstat')) return "📟 <strong>netstat</strong> : commande qui affiche les connexions réseau et ports ouverts sur une machine.";
if (lowerMessage.includes('mtr')) return "🛣️ <strong>MTR</strong> : outil combinant traceroute et ping pour diagnostiquer le chemin réseau.";
if (lowerMessage.includes('monitoring réseau') || lowerMessage.includes('supervision réseau')) return "👁️ <strong>Monitoring réseau</strong> : surveillance continue pour détecter pannes et anomalies.";

// 151-160 : diagnostics et dépannage
if (lowerMessage.includes('ping')) return "🏓 <strong>Ping</strong> : test d’accessibilité d’un hôte en mesurant le temps aller-retour (RTT).";
if (lowerMessage.includes('traceroute') || lowerMessage.includes('tracert')) return "🧭 <strong>Traceroute</strong> : outil pour lister les routeurs traversés entre deux hôtes.";
if (lowerMessage.includes('nslookup') || lowerMessage.includes('dig')) return "📛 <strong>nslookup / dig</strong> : outils pour interroger les serveurs DNS et diagnostiquer la résolution.";
if (lowerMessage.includes('arp -a') || lowerMessage.includes('arp command')) return "🔎 <strong>Commande ARP</strong> : permet de voir les correspondances IP↔MAC sur une machine.";
if (lowerMessage.includes('flush dns') || lowerMessage.includes('vider cache dns')) return "🧹 <strong>Vider le cache DNS</strong> : rafraîchir la résolution DNS locale en supprimant les entrées mises en cache.";
if (lowerMessage.includes('reboot routeur') || lowerMessage.includes('redemarrer routeur')) return "🔁 <strong>Reboot routeur</strong> : redémarrer un équipement pour résoudre des problèmes temporaires.";
if (lowerMessage.includes('analyse packet loss') || lowerMessage.includes('packet loss')) return "❌ <strong>Perte de paquets</strong> : pourcentage de paquets perdus, signe de congestion ou d’erreurs physiques.";
if (lowerMessage.includes('latence') || lowerMessage.includes('latency')) return "⏱️ <strong>Latence</strong> : délai entre l’envoi et la réception d’un paquet (importante pour le temps réel).";
if (lowerMessage.includes('jitter')) return "🎚️ <strong>Jitter</strong> : variation de latence entre paquets, pénalisant pour la voix/vidéo.";
if (lowerMessage.includes('mtu')) return "📏 <strong>MTU</strong> : taille maximale d’un paquet que le réseau peut transporter sans fragmentation.";

// 161-170 : virtualisation et cloud networking
if (lowerMessage.includes('vlan tagging') || lowerMessage.includes('tagging')) return "🏷️ <strong>Tagging</strong> : marquage des trames pour indiquer leur VLAN sur un lien trunk.";
if (lowerMessage.includes('vnic') || lowerMessage.includes('virtual nic')) return "🖧 <strong>vNIC</strong> : interface réseau virtuelle attachée à une machine virtuelle.";
if (lowerMessage.includes('vps')) return "☁️ <strong>VPS</strong> : serveur virtuel privé loué chez un hébergeur.";
if (lowerMessage.includes('vswitch') || lowerMessage.includes('v switch')) return "🛠️ <strong>vSwitch</strong> : switch virtuel qui relie des vNICs dans un hyperviseur.";
if (lowerMessage.includes('vxlan')) return "🕸️ <strong>VXLAN</strong> : encapsulation qui crée un overlay réseau pour isoler le trafic multitenant.";
if (lowerMessage.includes('sdn')) return "🧠 <strong>SDN</strong> : Software‑Defined Networking — séparation du contrôle et du plan de données pour une gestion programmée.";
if (lowerMessage.includes('nfv')) return "🔁 <strong>NFV</strong> : Network Functions Virtualization — virtualiser des fonctions réseau (firewall, load balancer…).";
if (lowerMessage.includes('overlay network') || lowerMessage.includes('overlay')) return "☁️ <strong>Overlay</strong> : réseau logique construit sur un réseau physique (underlay).";
if (lowerMessage.includes('service discovery')) return "🔎 <strong>Service Discovery</strong> : mécanisme pour trouver automatiquement services et adresses dans un cluster.";
if (lowerMessage.includes('cni plugin') || lowerMessage.includes('cni')) return "🔌 <strong>Plugin CNI</strong> : connecte des conteneurs à un réseau dans Kubernetes.";

// 171-180 : voip, temps réel et multimedia
if (lowerMessage.includes('voip')) return "📞 <strong>VoIP</strong> : transmission de la voix sur IP (téléphonie via Internet).";
if (lowerMessage.includes('sip')) return "📶 <strong>SIP</strong> : protocole pour établir des appels VoIP (signalisation).";
if (lowerMessage.includes('rtp')) return "🎧 <strong>RTP</strong> : protocole pour transporter l’audio/vidéo en temps réel.";
if (lowerMessage.includes('rtcp')) return "📊 <strong>RTCP</strong> : protocole compagnon de RTP pour supervision et statistique.";
if (lowerMessage.includes('sbc') || lowerMessage.includes('session border controller')) return "🛡️ <strong>SBC</strong> : appareil qui sécurise et contrôle les flux VoIP entre réseaux.";
if (lowerMessage.includes('mos') || lowerMessage.includes('mean opinion score')) return "⭐ <strong>MOS</strong> : score de qualité perçue d’un appel VoIP (0-5).";
if (lowerMessage.includes('jitter buffer')) return "🧰 <strong>Jitter Buffer</strong> : mémoire tampon pour compenser le jitter dans la lecture audio.";
if (lowerMessage.includes('codec')) return "🎚️ <strong>Codec</strong> : algorithme qui compresse/décompresse l’audio ou la vidéo (ex : G.711, Opus).";
if (lowerMessage.includes('latence reseau voix') || lowerMessage.includes('latence voip')) return "⏳ <strong>Latence VoIP</strong> : délai critique pour la conversation en temps réel (idéalement <150 ms).";
if (lowerMessage.includes('pbx')) return "🏢 <strong>PBX</strong> : central téléphonique (physique ou virtuel) gérant les appels d’une entreprise.";

// 181-190 : CDN, cache et performance
if (lowerMessage.includes('cdn')) return "🚀 <strong>CDN</strong> : réseau de serveurs qui met en cache le contenu pour le rapprocher des utilisateurs.";
if (lowerMessage.includes('cache')) return "🗄️ <strong>Cache</strong> : stockage temporaire pour accélérer l’accès aux données fréquemment demandées.";
if (lowerMessage.includes('ttl dns') || lowerMessage.includes('ttl')) return "⏳ <strong>TTL</strong> : durée de vie d’une entrée DNS ou d’un paquet (Time To Live).";
if (lowerMessage.includes('edge server') || lowerMessage.includes('edge')) return "🖥️ <strong>Edge Server</strong> : serveur proche de l’utilisateur pour réduire la latence.";
if (lowerMessage.includes('compresssion http') || lowerMessage.includes('compression')) return "📦 <strong>Compression</strong> : réduire la taille des données envoyées pour améliorer les performances.";
if (lowerMessage.includes('keep alive') || lowerMessage.includes('keep-alive')) return "🔁 <strong>Keep-Alive</strong> : garder une connexion TCP ouverte pour réutiliser la même session et gagner du temps.";
if (lowerMessage.includes('http2')) return "⚡ <strong>HTTP/2</strong> : version du protocole HTTP plus performante (multiplexing, poussée serveur).";
if (lowerMessage.includes('http3')) return "🚀 <strong>HTTP/3</strong> : HTTP sur QUIC pour réduire la latence (transport via UDP).";
if (lowerMessage.includes('quic')) return "🏎️ <strong>QUIC</strong> : protocole transport rapide basé sur UDP pour optimiser les connexions Web.";
if (lowerMessage.includes('cache control') || lowerMessage.includes('cache-control')) return "🧾 <strong>Cache-Control</strong> : en-tête HTTP qui indique comment et combien de temps cacher une ressource.";

// 191-200 : pratiques, concepts finaux et outils complémentaires
if (lowerMessage.includes('haute disponibilite') || lowerMessage.includes('haute disponibilité')) return "💡 <strong>Haute disponibilité</strong> : architecture pour minimiser les interruptions de service.";
if (lowerMessage.includes('scalabilite') || lowerMessage.includes('scalabilité')) return "📈 <strong>Scalabilité</strong> : capacité d’un système à gérer une augmentation de charge.";
if (lowerMessage.includes('autoscaling')) return "⚙️ <strong>Autoscaling</strong> : ajuster automatiquement les ressources selon la charge (cloud).";
if (lowerMessage.includes('backhaul')) return "🔗 <strong>Backhaul</strong> : liaison qui transporte le trafic d’un point d’accès vers le cœur du réseau.";
if (lowerMessage.includes('internet exchange') || lowerMessage.includes('ixp')) return "🤝 <strong>IXP</strong> : lieu physique où les opérateurs échangent du trafic directement (peering).";
if (lowerMessage.includes('snmp community') || lowerMessage.includes('community string')) return "🔑 <strong>SNMP Community</strong> : mot de passe simple pour accéder aux données SNMP (à sécuriser).";
if (lowerMessage.includes('hairpin nat')) return "🔁 <strong>Hairpin NAT</strong> : technique qui permet aux clients internes d’accéder à un service interne via l’IP publique du routeur.";
if (lowerMessage.includes('port mirroring') || lowerMessage.includes('span')) return "🔍 <strong>Port mirroring</strong> : copie du trafic d’un port vers un autre pour analyser le trafic.";
if (lowerMessage.includes('bonding') || lowerMessage.includes('link aggregation') || lowerMessage.includes('lacp')) return "🔗 <strong>Link Aggregation / LACP</strong> : regrouper plusieurs liens physiques pour augmenter le débit et la redondance.";
if (lowerMessage.includes('documentation reseau') || lowerMessage.includes('doc reseau')) return "📘 <strong>Documentation réseau</strong> : schémas, adresses et procédures pour comprendre et gérer l’infrastructure.";
// ========== BASES DU CLOUD (40 définitions) ==========

if (lowerMessage.includes('cloud')) return "☁️ <strong>Cloud</strong> : ensemble de serveurs accessibles sur Internet pour stocker et exécuter des services.";
if (lowerMessage.includes('cloud computing')) return "⚙️ <strong>Cloud Computing</strong> : utilisation de ressources informatiques à distance via Internet.";
if (lowerMessage.includes('serveur')) return "🖥️ <strong>Serveur</strong> : ordinateur puissant hébergeant sites web ou applications.";
if (lowerMessage.includes('data center')) return "🏢 <strong>Data Center</strong> : lieu physique où sont regroupés les serveurs du cloud.";
if (lowerMessage.includes('stockage cloud')) return "💾 <strong>Stockage cloud</strong> : espace en ligne pour sauvegarder tes fichiers et y accéder partout.";
if (lowerMessage.includes('virtualisation')) return "🪄 <strong>Virtualisation</strong> : technique qui permet de faire tourner plusieurs machines virtuelles sur un même serveur.";
if (lowerMessage.includes('machine virtuelle')) return "💻 <strong>Machine virtuelle</strong> : ordinateur simulé à l’intérieur d’un autre, souvent utilisé dans le cloud.";
if (lowerMessage.includes('conteneur')) return "📦 <strong>Conteneur</strong> : environnement léger et isolé pour exécuter des applications.";
if (lowerMessage.includes('kubernetes')) return "☸️ <strong>Kubernetes</strong> : outil qui gère automatiquement les conteneurs sur plusieurs serveurs.";
if (lowerMessage.includes('docker')) return "🐳 <strong>Docker</strong> : plateforme qui simplifie la création et le déploiement de conteneurs.";

if (lowerMessage.includes('saas')) return "📦 <strong>SaaS</strong> : logiciel disponible en ligne sans installation (ex : Gmail, Canva).";
if (lowerMessage.includes('paas')) return "🧱 <strong>PaaS</strong> : plateforme cloud qui fournit tout le nécessaire pour développer et déployer des applis.";
if (lowerMessage.includes('iaas')) return "🏗️ <strong>IaaS</strong> : service qui loue serveurs, stockage et réseau à la demande.";
if (lowerMessage.includes('faaS') || lowerMessage.includes('serverless')) return "⚡ <strong>Serverless / FaaS</strong> : exécution de code à la demande sans gérer les serveurs.";
if (lowerMessage.includes('cloud public')) return "🌥️ <strong>Cloud public</strong> : services partagés entre plusieurs clients via Internet.";
if (lowerMessage.includes('cloud prive')) return "🔒 <strong>Cloud privé</strong> : infrastructure dédiée à une seule organisation.";
if (lowerMessage.includes('cloud hybride')) return "🌩️ <strong>Cloud hybride</strong> : mélange entre cloud privé et public pour plus de flexibilité.";
if (lowerMessage.includes('multi cloud')) return "🌤️ <strong>Multi-cloud</strong> : utilisation de plusieurs fournisseurs cloud en même temps.";
if (lowerMessage.includes('scalabilite')) return "📈 <strong>Scalabilité</strong> : capacité d’un système à s’adapter à la charge (plus d’utilisateurs ou données).";
if (lowerMessage.includes('elasticite')) return "🧘 <strong>Élasticité</strong> : capacité à augmenter ou réduire automatiquement les ressources selon la demande.";

if (lowerMessage.includes('aws')) return "🟧 <strong>AWS</strong> : Amazon Web Services, principal fournisseur de services cloud au monde.";
if (lowerMessage.includes('azure')) return "🔷 <strong>Microsoft Azure</strong> : plateforme cloud de Microsoft pour héberger et gérer des applications.";
if (lowerMessage.includes('google cloud')) return "🟦 <strong>Google Cloud</strong> : services cloud proposés par Google pour stockage, IA et data.";
if (lowerMessage.includes('ovh')) return "🇫🇷 <strong>OVHcloud</strong> : fournisseur cloud français proposant hébergement et serveurs.";
if (lowerMessage.includes('oracle cloud')) return "🟥 <strong>Oracle Cloud</strong> : solution cloud axée sur les bases de données et entreprises.";
if (lowerMessage.includes('ibm cloud')) return "⚫ <strong>IBM Cloud</strong> : offre cloud hybride et IA pour entreprises.";
if (lowerMessage.includes('alibaba cloud')) return "🐉 <strong>Alibaba Cloud</strong> : principal fournisseur cloud en Asie.";
if (lowerMessage.includes('heroku')) return "🚀 <strong>Heroku</strong> : plateforme simple pour déployer des applications web.";
if (lowerMessage.includes('cloudflare')) return "🌐 <strong>Cloudflare</strong> : service pour accélérer les sites web et les protéger des attaques.";
if (lowerMessage.includes('digitalocean')) return "🌊 <strong>DigitalOcean</strong> : fournisseur cloud simple et abordable pour les développeurs.";

if (lowerMessage.includes('haute disponibilite')) return "💡 <strong>Haute disponibilité</strong> : capacité d’un service à rester en ligne même en cas de panne.";
if (lowerMessage.includes('load balancing')) return "⚖️ <strong>Load Balancing</strong> : répartition du trafic entre plusieurs serveurs pour éviter la surcharge.";
if (lowerMessage.includes('backup')) return "💽 <strong>Backup</strong> : sauvegarde des données stockées dans le cloud.";
if (lowerMessage.includes('disaster recovery')) return "🆘 <strong>Disaster Recovery</strong> : plan pour restaurer les services après une panne majeure.";
if (lowerMessage.includes('cdn')) return "🌎 <strong>CDN</strong> : réseau de serveurs qui distribue le contenu plus rapidement selon la localisation.";
if (lowerMessage.includes('latence')) return "⏱️ <strong>Latence</strong> : délai entre la demande d’un utilisateur et la réponse du serveur.";
if (lowerMessage.includes('api')) return "🔌 <strong>API</strong> : interface qui permet à deux programmes de communiquer.";
if (lowerMessage.includes('billing') || lowerMessage.includes('facturation')) return "💰 <strong>Facturation cloud</strong> : paiement à l’usage selon les ressources consommées.";
if (lowerMessage.includes('securite cloud')) return "🛡️ <strong>Sécurité cloud</strong> : ensemble de pratiques pour protéger les données et services en ligne.";
if (lowerMessage.includes('compliance')) return "📋 <strong>Conformité</strong> : respect des lois et normes pour le stockage et la gestion des données.";

if (lowerMessage.includes('monitoring')) return "📊 <strong>Monitoring</strong> : surveillance des performances et de la santé des services cloud.";
if (lowerMessage.includes('devops')) return "🧩 <strong>DevOps</strong> : méthode qui rapproche développeurs et administrateurs pour livrer plus vite.";
if (lowerMessage.includes('infrastructure as code') || lowerMessage.includes('iac')) return "📜 <strong>Infrastructure as Code</strong> : gestion automatique des serveurs avec du code.";
if (lowerMessage.includes('cloud provider')) return "🏢 <strong>Cloud Provider</strong> : entreprise qui propose des services cloud (AWS, Azure, GCP…).";
if (lowerMessage.includes('region cloud')) return "🗺️ <strong>Région Cloud</strong> : zone géographique où sont hébergés tes serveurs.";
if (lowerMessage.includes('instance')) return "🧩 <strong>Instance</strong> : machine virtuelle en cours d’exécution dans le cloud.";
if (lowerMessage.includes('scaling automatique')) return "📈 <strong>Auto-scaling</strong> : augmentation automatique des ressources selon le trafic.";
if (lowerMessage.includes('sla')) return "📃 <strong>SLA</strong> : contrat qui garantit un niveau minimal de service entre client et fournisseur.";
if (lowerMessage.includes('cloud natif')) return "🌱 <strong>Cloud natif</strong> : applications conçues dès le départ pour fonctionner dans le cloud.";
if (lowerMessage.includes('migration cloud')) return "🚚 <strong>Migration vers le cloud</strong> : transfert des applications et données depuis un serveur local vers le cloud.";
// ========== DATA SCIENCE (40 définitions) ==========

if (lowerMessage.includes('data science')) return "📊 <strong>Data Science</strong> : discipline qui consiste à analyser et interpréter les données pour en tirer des informations utiles.";
if (lowerMessage.includes('data scientist')) return "🧠 <strong>Data Scientist</strong> : expert qui combine statistiques, programmation et analyse pour créer des modèles prédictifs.";
if (lowerMessage.includes('data analyst')) return "📈 <strong>Data Analyst</strong> : professionnel qui étudie les données et crée des rapports pour aider à la prise de décision.";
if (lowerMessage.includes('data engineer')) return "🛠️ <strong>Data Engineer</strong> : spécialiste qui construit les pipelines et systèmes permettant de collecter et transformer les données.";
if (lowerMessage.includes('machine learning')) return "🤖 <strong>Machine Learning</strong> : technique où les ordinateurs apprennent à partir de données sans être explicitement programmés.";
if (lowerMessage.includes('deep learning')) return "🧩 <strong>Deep Learning</strong> : sous-domaine du machine learning utilisant des réseaux de neurones profonds.";
if (lowerMessage.includes('ia') || lowerMessage.includes('intelligence artificielle')) return "💡 <strong>Intelligence Artificielle</strong> : ensemble de méthodes pour faire réfléchir les machines comme des humains.";
if (lowerMessage.includes('statistique')) return "📉 <strong>Statistiques</strong> : science des données qui permet d’analyser et de résumer les informations.";
if (lowerMessage.includes('prediction')) return "🔮 <strong>Prédiction</strong> : estimation de ce qui pourrait se produire à partir des données passées.";
if (lowerMessage.includes('modele')) return "⚙️ <strong>Modèle</strong> : représentation mathématique qui apprend à faire des prédictions sur de nouvelles données.";

if (lowerMessage.includes('entrainement')) return "🏋️ <strong>Entraînement</strong> : phase où un modèle apprend à partir des données.";
if (lowerMessage.includes('test')) return "🧪 <strong>Test</strong> : étape où l’on vérifie si le modèle prédit correctement sur des données nouvelles.";
if (lowerMessage.includes('validation')) return "✅ <strong>Validation</strong> : processus pour évaluer la qualité d’un modèle avant sa mise en production.";
if (lowerMessage.includes('donnees')) return "💾 <strong>Données</strong> : informations brutes collectées à partir de différentes sources.";
if (lowerMessage.includes('dataset') || lowerMessage.includes('jeu de donnees')) return "🗃️ <strong>Dataset</strong> : ensemble structuré de données utilisées pour l’analyse ou l’apprentissage.";
if (lowerMessage.includes('nettoyage de donnees')) return "🧹 <strong>Nettoyage de données</strong> : étape qui consiste à corriger ou supprimer les erreurs dans les données.";
if (lowerMessage.includes('feature')) return "📋 <strong>Feature</strong> : variable ou caractéristique utilisée pour entraîner un modèle prédictif.";
if (lowerMessage.includes('target')) return "🎯 <strong>Target</strong> : valeur que le modèle doit prédire (ex : prix, note, catégorie).";
if (lowerMessage.includes('supervise')) return "👩‍🏫 <strong>Apprentissage supervisé</strong> : apprentissage à partir de données étiquetées (avec réponses connues).";
if (lowerMessage.includes('non supervise')) return "🕵️ <strong>Apprentissage non supervisé</strong> : apprentissage sans étiquettes, pour découvrir des structures cachées.";

if (lowerMessage.includes('classification')) return "🧮 <strong>Classification</strong> : tâche qui consiste à prédire une catégorie (ex : spam ou non spam).";
if (lowerMessage.includes('regression')) return "📈 <strong>Régression</strong> : prédiction d’une valeur numérique (ex : prix, température).";
if (lowerMessage.includes('clustering')) return "🔗 <strong>Clustering</strong> : regroupement automatique de données similaires (ex : clients similaires).";
if (lowerMessage.includes('k means')) return "⚪ <strong>K-Means</strong> : algorithme simple de clustering qui regroupe les données en k groupes.";
if (lowerMessage.includes('arbre de decision')) return "🌳 <strong>Arbre de décision</strong> : modèle qui prend des décisions en suivant un arbre de choix.";
if (lowerMessage.includes('random forest')) return "🌲 <strong>Random Forest</strong> : ensemble d’arbres de décision pour de meilleures prédictions.";
if (lowerMessage.includes('regression lineaire')) return "📉 <strong>Régression linéaire</strong> : modèle qui prédit une valeur à partir d’une droite de tendance.";
if (lowerMessage.includes('bayes')) return "🎲 <strong>Naive Bayes</strong> : modèle basé sur les probabilités, souvent utilisé pour le tri de texte.";
if (lowerMessage.includes('svm')) return "⚔️ <strong>SVM</strong> : algorithme qui sépare les données selon la meilleure frontière possible.";
if (lowerMessage.includes('k nearest neighbors') || lowerMessage.includes('knn')) return "👥 <strong>KNN</strong> : algorithme qui classe une donnée selon ses voisins les plus proches.";

if (lowerMessage.includes('feature engineering')) return "🧩 <strong>Feature Engineering</strong> : création de nouvelles variables pour améliorer la performance d’un modèle.";
if (lowerMessage.includes('normalisation')) return "📏 <strong>Normalisation</strong> : mise à l’échelle des données pour que chaque variable ait la même importance.";
if (lowerMessage.includes('overfitting')) return "🌀 <strong>Overfitting</strong> : quand un modèle apprend trop les détails du jeu d’entraînement et devient moins performant.";
if (lowerMessage.includes('underfitting')) return "📉 <strong>Underfitting</strong> : quand un modèle est trop simple et ne comprend pas bien les données.";
if (lowerMessage.includes('cross validation')) return "🔁 <strong>Cross-validation</strong> : technique pour tester la fiabilité d’un modèle sur plusieurs sous-ensembles de données.";
if (lowerMessage.includes('accuracy')) return "🎯 <strong>Accuracy</strong> : mesure qui indique le pourcentage de bonnes prédictions d’un modèle.";
if (lowerMessage.includes('precision')) return "📊 <strong>Précision</strong> : proportion de vraies prédictions positives parmi toutes les prédictions positives.";
if (lowerMessage.includes('recall')) return "📈 <strong>Recall</strong> : capacité du modèle à retrouver toutes les données pertinentes.";
if (lowerMessage.includes('f1 score')) return "⚖️ <strong>F1 Score</strong> : moyenne entre précision et rappel pour évaluer la qualité d’un modèle.";
if (lowerMessage.includes('matrice de confusion')) return "🔲 <strong>Matrice de confusion</strong> : tableau qui montre les bonnes et mauvaises prédictions d’un modèle.";

if (lowerMessage.includes('pandas')) return "🐼 <strong>Pandas</strong> : bibliothèque Python pour manipuler les données facilement.";
if (lowerMessage.includes('numpy')) return "🔢 <strong>NumPy</strong> : bibliothèque Python pour le calcul scientifique et les matrices.";
if (lowerMessage.includes('matplotlib')) return "📊 <strong>Matplotlib</strong> : bibliothèque Python pour créer des graphiques et visualiser les données.";
if (lowerMessage.includes('seaborn')) return "🌊 <strong>Seaborn</strong> : outil de visualisation pour créer des graphiques statistiques élégants.";
if (lowerMessage.includes('jupyter')) return "📓 <strong>Jupyter Notebook</strong> : environnement interactif pour coder, tester et visualiser les données.";
if (lowerMessage.includes('sql')) return "🗄️ <strong>SQL</strong> : langage qui permet d’interroger et manipuler des bases de données.";
if (lowerMessage.includes('big data')) return "🌐 <strong>Big Data</strong> : ensemble massif de données qu’on ne peut traiter qu’avec des outils spécialisés.";
if (lowerMessage.includes('etl')) return "🔄 <strong>ETL</strong> : processus d’Extraction, Transformation et Chargement des données vers un entrepôt.";
if (lowerMessage.includes('data lake')) return "🏞️ <strong>Data Lake</strong> : espace où sont stockées toutes les données brutes avant analyse.";
if (lowerMessage.includes('data warehouse')) return "🏢 <strong>Data Warehouse</strong> : base de données centralisée contenant des données prêtes pour l’analyse.";

// ========== RÉPONSES SIMPLES / CONVERSATIONNELLES ==========

// Salutations
if (lowerMessage.includes('bonjour')) return "👋 Bonjour ! Comment vas-tu aujourd’hui ?";
if (lowerMessage.includes('salut')) return "😄 Salut à toi ! Ça fait plaisir de te voir ici.";
if (lowerMessage.includes('bonsoir')) return "🌙 Bonsoir ! J’espère que ta journée s’est bien passée.";
if (lowerMessage.includes('bonne nuit')) return "😴 Bonne nuit 🌙 ! Fais de beaux rêves et repose-toi bien.";
if (lowerMessage.includes('yo')) return "✌️ Yo ! Prêt à parler un peu de tech ou juste chill ?";
if (lowerMessage.includes('coucou')) return "👋 Coucou 😄 ! Comment tu vas ?";

// “Ça va ?”
if (lowerMessage.includes('ça va') || lowerMessage.includes('ca va')) return "😊 Ça va super bien, merci ! Et toi, comment tu vas ?";
if (lowerMessage.includes('je vais bien')) return "Super 😄 ! Content de savoir que tout va bien.";
if (lowerMessage.includes('pas bien')) return "😔 Oh mince… si tu veux, on peut discuter un peu pour te changer les idées.";
if (lowerMessage.includes('fatigué') || lowerMessage.includes('fatigue')) return "💤 Courage ! Un peu de repos et ça repart !";

// Politesse
if (lowerMessage.includes('merci')) return "🙏 Avec plaisir ! Je suis là pour ça 😄";
if (lowerMessage.includes('merci beaucoup')) return "🥰 De rien, ça me fait plaisir de t’aider.";
if (lowerMessage.includes('svp') || lowerMessage.includes('s’il te plaît')) return "😊 Bien sûr, je t’aide avec plaisir.";
if (lowerMessage.includes('de rien')) return "😄 Avec plaisir ! On forme une bonne équipe toi et moi !";

// Départ
if (lowerMessage.includes('au revoir')) return "👋 Au revoir ! À très bientôt !";
if (lowerMessage.includes('a plus') || lowerMessage.includes('à plus')) return "👋 À plus tard ! Passe une super journée 😄";
if (lowerMessage.includes('bonne journée')) return "🌞 Merci ! Bonne journée à toi aussi !";
if (lowerMessage.includes('bonne soirée')) return "🌆 Merci ! Passe une excellente soirée !";
if (lowerMessage.includes('bonne nuit')) return "🌙 Bonne nuit ! Repose-toi bien 😴";

// Humeur
if (lowerMessage.includes('je suis content') || lowerMessage.includes('je suis heureux')) return "😄 Trop bien ! J’adore quand tu es de bonne humeur !";
if (lowerMessage.includes('je suis triste')) return "😢 Oh… ça va aller, parle-moi si tu veux, je suis là pour toi.";
if (lowerMessage.includes('je m’ennuie') || lowerMessage.includes('je menui')) return "🤔 Tu veux que je te raconte un fait intéressant sur la tech ?";
if (lowerMessage.includes('cool')) return "😎 Carrément cool !";

// Présentation
if (lowerMessage.includes('qui es tu')) return "🤖 Je suis ton chatbot, toujours prêt à discuter ou à t’expliquer des trucs intéressants !";
if (lowerMessage.includes('comment tu t’appelles')) return "💬 Moi ? On peut m’appeler comme tu veux ! Et toi, c’est quoi ton prénom ?";
if (lowerMessage.includes('que fais tu')) return "⚙️ J’analyse ce que tu me dis et j’essaie de te répondre le plus naturellement possible 😄";
if (lowerMessage.includes('d’ou viens tu')) return "🌐 Je viens du monde du code et du cloud ☁️ !";

// Temps / météo / humeur légère
if (lowerMessage.includes('quelle heure') || lowerMessage.includes('heure est il')) return "⏰ Je ne porte pas de montre, mais il est toujours l’heure de coder 😄";
if (lowerMessage.includes('il fait beau')) return "🌞 Génial ! Le beau temps, c’est bon pour le moral.";
if (lowerMessage.includes('il pleut')) return "🌧️ Parfait pour rester au chaud et apprendre un peu de tech 😉";
if (lowerMessage.includes('je t’aime')) return "🥰 Ohhh, c’est gentil ! Moi aussi je t’aime bien, humain curieux 💡";
if (lowerMessage.includes('tu es la')) return "🙋 Oui je suis là ! Toujours prêt à discuter ou t’aider.";

// Autres
if (lowerMessage.includes('lol') || lowerMessage.includes('mdr')) return "😂 Haha ! Tu m’as bien fait rire aussi.";
if (lowerMessage.includes('bravo')) return "🏆 Merci beaucoup ! Mais le mérite te revient aussi 😉";
if (lowerMessage.includes('ok')) return "👍 Parfait ! On continue ?";
if (lowerMessage.includes('non')) return "😅 D’accord, pas de souci. On fait une pause ?";
if (lowerMessage.includes('oui')) return "😄 Super ! Dis-moi ce que tu veux faire ou apprendre.";
if (lowerMessage.includes('super')) return "✨ Merci ! Tu es au top aussi !";

// ========== 🧠 RÉPONSES DÉTAILLÉES / EXPLICATIVES ==========

// Modèles de Cloud
if (lowerMessage.includes('modèles de cloud') || lowerMessage.includes('modeles de cloud')) 
  return "☁️ Les modèles de cloud computing se divisent en trois grandes catégories :<br><br><strong>1. IaaS (Infrastructure as a Service)</strong> : tu loues des serveurs virtuels, du stockage et des réseaux. Tu gères tout toi-même, comme si tu avais ton propre data center.<br><br><strong>2. PaaS (Platform as a Service)</strong> : tu as une plateforme complète pour développer et déployer tes applications sans gérer les serveurs. Exemples : Heroku, Google App Engine.<br><br><strong>3. SaaS (Software as a Service)</strong> : tu utilises des logiciels déjà hébergés sur le cloud. Exemples : Gmail, Office 365, Zoom.<br><br>Chaque modèle offre un niveau de contrôle et de responsabilité différent, selon les besoins de ton entreprise ou projet.";

// Avantages du Cloud
if (lowerMessage.includes('avantages du cloud')) 
  return "🌍 Les avantages du cloud computing sont nombreux :<br><br>• <strong>Évolutivité</strong> : tu peux augmenter ou réduire les ressources selon les besoins.<br>• <strong>Accessibilité</strong> : tes données et applis sont accessibles partout, tant que tu as Internet.<br>• <strong>Coût</strong> : pas besoin d’acheter du matériel, tu payes seulement ce que tu utilises.<br>• <strong>Sécurité</strong> : les grands fournisseurs proposent des outils de protection avancés.<br>• <strong>Sauvegarde automatique</strong> : tes données sont souvent sauvegardées en continu.";

// Inconvénients du Cloud
if (lowerMessage.includes('inconvénients du cloud') || lowerMessage.includes('inconvenients du cloud')) 
  return "⚠️ Le cloud computing a aussi quelques limites :<br><br>• <strong>Dépendance à Internet</strong> : sans connexion, tu ne peux pas accéder à tes services.<br>• <strong>Sécurité des données</strong> : elles sont hébergées chez un tiers, donc il faut faire confiance au fournisseur.<br>• <strong>Coûts à long terme</strong> : les petits paiements mensuels peuvent devenir importants sur la durée.<br>• <strong>Moins de contrôle</strong> : tu ne gères pas l’infrastructure physique, donc tu dépends du fournisseur.";

// Fournisseurs de Cloud
if (lowerMessage.includes('fournisseurs de cloud')) 
  return "🏢 Les principaux fournisseurs de cloud sont :<br><br>• <strong>Amazon Web Services (AWS)</strong> : le leader mondial, très complet.<br>• <strong>Microsoft Azure</strong> : bon choix pour les entreprises déjà sur Windows.<br>• <strong>Google Cloud Platform (GCP)</strong> : puissant pour la data et l’IA.<br>• <strong>IBM Cloud</strong> : orienté entreprise et hybride.<br>• <strong>Oracle Cloud</strong> : spécialisé dans les bases de données.<br><br>Chacun propose des offres adaptées à différents besoins et budgets.";

      return "🤔 Je n'ai pas encore appris ça ! Pose-moi une question sur l'informatique, les réseaux, la programmation, la sécurité, l'IA, ou le cloud computing.";
    }

    // Ajouter les animations CSS
    const style = document.createElement('style');
    style.textContent = `
      @keyframes slideIn {
        from { transform: translateX(100%); opacity: 0; }
        to { transform: translateX(0); opacity: 1; }
      }
      
      @keyframes slideOut {
        from { transform: translateX(0); opacity: 1; }
        to { transform: translateX(100%); opacity: 0; }
      }
    `;
    document.head.appendChild(style);
  </script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</body>
</html>

