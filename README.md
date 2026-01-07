<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>RK Club Tournament</title>

    <!-- Icons and Fonts -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700;900&display=swap" rel="stylesheet">
    <!-- Swiper CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

    <style>
        :root {
            --primary-bg: #121212;
            --secondary-bg: #1E1E1E;
            --card-bg: #1E1E1E;
            --text-primary: #EAEAEA;
            --text-secondary: #AAAAAA;
            --accent-color: #00A8FF;
            --accent-gradient: linear-gradient(to right, #00A8FF, #0077B6);
            --primary-button-bg: #00A8FF;
            --border-color: #333333;
            --bottom-nav-bg: #1E1E1E;
            --success-color: #10B981;
            --danger-color: #EF4444;
            --warning-color: #F59E0B;
            --info-color: #3B82F6;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { font-size: 16px; }
        body { font-family: 'Poppins', sans-serif; background-color: var(--primary-bg); color: var(--text-primary); padding-top: 70px; padding-bottom: 110px; min-height: 100vh; overscroll-behavior-y: contain; }
        a { color: var(--accent-color); text-decoration: none; } a:hover { color: #0077B6; }
        .main-content { padding: 15px; } .section { display: none; animation: fadeIn 0.3s ease-in-out; } .section.active { display: block; } @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        .section-title { font-size: 1.1rem; font-weight: 600; margin-bottom: 15px; color: var(--text-primary); } .custom-card { background-color: var(--card-bg); border-radius: 12px; padding: 15px; margin-bottom: 15px; box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2); border: 1px solid var(--border-color); }
        .btn-custom { border-radius: 8px; font-size: 0.9rem; font-weight: 600; padding: 10px 15px; border: none; display: inline-flex; align-items: center; justify-content: center; gap: 5px; transition: all 0.2s ease; }
        .btn-custom-primary { background-color: var(--primary-button-bg); color: #FFFFFF; }
        .btn-custom-primary:hover { filter: brightness(1.2); transform: translateY(-1px); }
        .btn-custom-secondary { background-color: var(--secondary-bg); color: var(--text-primary); border: 1px solid var(--border-color); }
        .btn-custom-secondary:hover { background-color: #2c2c2c; border-color: #555555; }
        .btn-custom-accent { background: var(--accent-gradient); color: white; }
        .btn-custom-accent:hover { filter: brightness(1.1); transform: translateY(-1px); box-shadow: 0 4px 15px rgba(0, 168, 255, 0.2); }
        .btn-custom-link { background: none; border: none; color: var(--accent-color); font-size: 0.9rem; font-weight: 500; padding: 0; cursor: pointer; }
        .text-accent { color: var(--accent-color); } .text-success { color: var(--success-color); } .text-danger { color: var(--danger-color); } .text-warning { color: var(--warning-color); }
        .form-control { background-color: var(--primary-bg); border: 1px solid var(--border-color); color: var(--text-primary); border-radius: 6px; }
        .form-control:focus { background-color: var(--primary-bg); border-color: var(--accent-color); color: var(--text-primary); box-shadow: 0 0 0 0.2rem rgba(0, 168, 255, 0.25); }
        .form-control::placeholder { color: var(--text-secondary); opacity: 0.7; } .form-label { color: var(--text-secondary); font-size: 0.9rem; }
        .alert { border-radius: 6px; font-size: 0.9rem; }
        .list-group-item { background-color: transparent; color: var(--text-primary); border: none; border-bottom: 1px solid var(--border-color); padding: 15px; font-size: 0.95rem; transition: background-color 0.2s ease, color 0.2s ease; }
        .list-group-item:hover { background-color: rgba(0, 168, 255, 0.08); color: white; }
        .list-group-item:last-child { border-bottom: none; }
        .list-group-item i:first-child { color: var(--accent-color); margin-right: 15px; font-size: 1.1rem; width: 20px; text-align: center; }
        .list-group-item .fa-chevron-right { color: var(--text-secondary); font-size: 0.9rem; }
        #globalLoaderEl { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.6); display: flex; justify-content: center; align-items: center; z-index: 9999; display: none; }
        .spinner-border { color: var(--accent-color); width: 3rem; height: 3rem; }
        .placeholder-glow .placeholder { background-color: rgba(51, 65, 85, 0.5); animation: placeholder-glow 2s ease-in-out infinite; }
        .placeholder { background-color: rgba(60, 9, 108, 0.5); border-radius: 4px; }
        @keyframes placeholder-glow { 0% { background-color: rgba(51, 51, 51, 0.5); } 50% { background-color: rgba(51, 51, 51, 0.7); } 100% { background-color: rgba(51, 51, 51, 0.5); } }
        .interactive-list-item { cursor: pointer; } .referral-code { font-family: monospace; letter-spacing: 1px; user-select: all; }
        .app-header { position: fixed; top: 0; left: 0; width: 100%; height: 60px; background-color: var(--secondary-bg); display: flex; align-items: center; justify-content: space-between; padding: 0 15px; box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2); z-index: 1000; border-bottom: 1px solid var(--border-color); }
        .header-left { display: flex; align-items: center; gap: 10px; }
        .header-logo { width: 40px; height: 40px; border-radius: 50%; background-color: #fff; object-fit: cover; border: 2px solid var(--accent-color); }
        .header-title { font-size: 0.9rem; font-weight: 500; line-height: 1.2; }
        .header-title span { font-size: 0.75rem; color: var(--text-secondary); display: block; }
        .header-back-button { background: none; border: none; color: var(--text-primary); font-size: 1.4rem; margin-right: 5px; display: none; padding: 5px; }
        .header-right { display: flex; align-items: center; gap: 15px; }
        .notification-icon { font-size: 1.3rem; color: var(--text-primary); position: relative; background: none; border: none; padding: 0; }
        .notification-badge { position: absolute; top: -3px; right: -5px; background-color: var(--danger-color); color: white; font-size: 0.6rem; width: 15px; height: 15px; border-radius: 50%; display: flex; justify-content: center; align-items: center; font-weight: bold; }
        .wallet-chip { background: var(--accent-gradient); color: white; padding: 5px 12px; border-radius: 20px; display: flex; align-items: center; font-size: 0.85rem; font-weight: 700; border: none; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2); cursor: pointer; }
        .wallet-chip i { margin-right: 5px; font-size: 0.9rem; }
        .header-game-title { font-size: 1rem; font-weight: 600; color: var(--text-primary); margin-left: 10px; display: none; }
        .bottom-nav { position: fixed; bottom: 0; left: 0; width: 100%; height: 65px; background-color: var(--bottom-nav-bg); display: flex; justify-content: space-around; align-items: stretch; box-shadow: 0 -2px 5px rgba(0, 0, 0, 0.2); z-index: 1000; border-top: 1px solid var(--border-color); }
        .nav-item { display: flex; flex-direction: column; align-items: center; justify-content: center; color: var(--text-secondary); text-decoration: none; flex-grow: 1; padding: 8px 0; transition: color 0.2s ease, background-color 0.2s ease; border: none; background: none; cursor: pointer; font-size: 0.7rem; }
        .nav-item i { font-size: 1.4rem; margin-bottom: 4px; line-height: 1; transition: transform 0.2s ease; }
        .nav-item span { font-size: 0.7rem; font-weight: 500; line-height: 1; }
        .nav-item.active { color: var(--accent-color); }
        .nav-item.active i { transform: scale(1.1); filter: drop-shadow(0 0 5px var(--accent-color)); }
        .swiper-container#promotionSliderEl { width: 100%; height: 200px; border-radius: 10px; margin-bottom: 25px; --swiper-pagination-color: var(--accent-color); --swiper-pagination-bullet-inactive-color: var(--text-secondary); --swiper-pagination-bullet-size: 8px; }
        .swiper-slide { background-color: var(--secondary-bg); border-radius: 10px; } .swiper-slide img { display: block; width: 100%; height: 100%; object-fit: cover; border-radius: 10px; }
        
        .game-card { text-align: center; background-color: var(--card-bg); border-radius: 8px; overflow: hidden; padding: 0; border: 1px solid var(--border-color); cursor: pointer; transition: transform 0.2s ease, box-shadow 0.2s ease; }
        .game-card:hover { transform: translateY(-3px); box-shadow: 0 4px 15px rgba(0, 168, 255, 0.15); }
        .game-card img { width: 100%; aspect-ratio: 16 / 9; object-fit: cover; display: block; }
        .game-card span { display: block; padding: 12px 8px; font-weight: 700; font-size: 1.1rem; color: var(--text-primary); text-transform: uppercase; letter-spacing: 1px; text-shadow: 0 1px 3px rgba(0,0,0,0.5); }
        
        .tournament-tabs { display: flex; justify-content: space-around; background-color: var(--secondary-bg); padding: 5px; border-radius: 8px; margin-bottom: 15px; }
        .tab-item { color: var(--text-secondary); background: none; border: none; padding: 8px 10px; font-size: 0.85rem; font-weight: 600; border-radius: 6px; flex-grow: 1; text-align: center; cursor: pointer; transition: background-color 0.2s, color 0.2s; }
        .tab-item.active { background-color: var(--accent-color); color: #FFFFFF; }
        .tab-item i { margin-right: 5px; }
        .tournament-card { background-color: var(--card-bg); border-radius: 12px; margin-bottom: 15px; padding: 15px; border: 1px solid var(--border-color); }
        .tournament-card-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 5px; }
        .tournament-card-tags span { background-color: var(--primary-bg); color: var(--text-secondary); font-size: 0.7rem; font-weight: 500; padding: 3px 8px; border-radius: 4px; display: inline-block; border: 1px solid var(--border-color); margin-right: 4px; margin-bottom: 4px; }
        .tournament-card-timer { background-color: rgba(0, 168, 255, 0.1); color: var(--accent-color); font-size: 0.75rem; font-weight: 600; padding: 3px 8px; border-radius: 4px; }
        .tournament-card-title { font-size: 1rem; font-weight: 600; margin-bottom: 5px; display: flex; align-items: center; gap: 8px; color: var(--text-primary); }
        .tournament-card-title i { color: var(--accent-color); }
        .tournament-card-info { display: flex; justify-content: space-between; align-items: stretch; border-top: 1px dashed var(--border-color); border-bottom: 1px dashed var(--border-color); padding: 10px 0; margin: 10px 0; font-size: 0.8rem; }
        .info-item { text-align: center; flex: 1; padding: 0 5px; }
        .info-item span { display: block; color: var(--text-secondary); font-size: 0.7rem; margin-bottom: 2px; }
        .info-item strong { color: var(--text-primary); font-weight: 600; font-size: 0.9rem; }
        .info-item .prize-icon { color: var(--accent-color); font-size: 1.2rem; }
        .tournament-card-spots { font-size: 0.8rem; color: var(--text-secondary); margin-bottom: 15px; }
        .tournament-card-spots span { font-weight: 600; color: var(--accent-color); }
        .progress { height: 6px; background-color: var(--primary-bg); border-radius: 3px; overflow: hidden; }
        .progress-bar { background-color: var(--accent-color); transition: width 0.3s ease; }
        .tournament-card-actions { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 10px; }
        .tournament-card-actions .btn-sm { padding: 8px 10px; font-size: 0.85rem; width: 100%; }
        .tournament-card-actions .btn-join { background: var(--accent-gradient); color: white; font-weight: 700; grid-column: 2 / 3; }
        .tournament-card-actions .btn-details { background-color: var(--secondary-bg); border: 1px solid var(--border-color); grid-column: 1 / 2; }
        .tournament-card-actions .btn-joined { background-color: var(--success-color); color: var(--text-primary); opacity: 0.8; grid-column: 2 / 3; }
        .tournament-card-actions .btn-disabled { background-color: var(--secondary-bg); opacity: 0.6; cursor: not-allowed; grid-column: 2 / 3; }
        .btn-idpass { background: var(--accent-gradient); color: white; border: none; font-weight: 600; }
        .wallet-card { background: linear-gradient(145deg, var(--secondary-bg), var(--primary-bg)); border-radius: 10px; padding: 20px; border: 1px solid var(--border-color); }
        .wallet-card h2 { font-size: 1.2rem; font-weight: 600; margin-bottom: 25px; }
        .balance-item { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; padding-bottom: 15px; border-bottom: 1px dashed var(--border-color); }
        .balance-item:last-child { margin-bottom: 0; border-bottom: none; padding-bottom: 0; }
        .balance-item-label { font-size: 0.95rem; color: var(--text-secondary); }
        .balance-item-value { font-size: 1.1rem; font-weight: 600; }
        .balance-item-action { min-width: 100px; text-align: right; }
        .balance-item-action .btn-custom-link { font-size: 0.85rem; color: var(--accent-color); padding: 5px; }
        .balance-item-action .btn-withdraw { background-color: var(--accent-color); color: white; font-weight: 600; font-size: 0.8rem; padding: 5px 12px; border-radius: 5px; border: none; }
        #recentTransactionsListEl .custom-card { background-color: var(--secondary-bg); }
        #earnings-section .custom-card { text-align: center; }
        #earnings-section .display-4 { font-size: 3.5rem; }
        #earnings-section p strong { color: var(--text-primary); }
        .profile-header-card { background: linear-gradient(145deg, var(--secondary-bg), var(--primary-bg)); border-radius: 10px; padding: 20px; display: flex; flex-direction: column; align-items: center; text-align: center; margin-bottom: 20px; border: 1px solid var(--border-color); }
        .profile-avatar { width: 70px; height: 70px; border-radius: 50%; margin-bottom: 10px; border: 2px solid var(--accent-color); object-fit: cover; background-color: var(--primary-bg); }
        .profile-name { font-size: 1.1rem; font-weight: 600; margin-bottom: 2px; }
        .profile-email { font-size: 0.85rem; color: var(--text-secondary); margin-bottom: 15px; word-break: break-all; }
        .profile-stats { display: flex; justify-content: space-around; width: 100%; border-top: 1px solid var(--border-color); padding-top: 15px; }
        .stat-item { text-align: center; flex: 1; } .stat-item strong { display: block; font-size: 1rem; font-weight: 600; }
        .stat-item span { font-size: 0.75rem; color: var(--text-secondary); }
        .profile-links .list-group { border-radius: 10px; overflow: hidden; border: 1px solid var(--border-color); background-color: var(--card-bg); }
        .profile-links .form-switch .form-check-input { background-color: var(--secondary-bg); border-color: var(--border-color); background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'%3e%3ccircle r='3' fill='rgba%28255, 255, 255, 0.25%29'/%3e%3c/svg%3e"); }
        .profile-links .form-switch .form-check-input:checked { background-color: var(--accent-color); border-color: var(--accent-color); background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='-4 -4 8 8'%3e%3ccircle r='3' fill='%23fff'/%3e%3c/svg%3e"); }
        #login-section { margin-top: 5vh; }
        #login-section .card { background-color: var(--card-bg); border: 1px solid var(--border-color); }
        #login-section .btn-primary { background-color: var(--primary-button-bg); border: none; color: white; font-weight: 600;}
        #login-section .btn-link { background: none; border: none; color: var(--accent-color); text-decoration: none; font-size: 0.9em; padding: 5px 0; }
        #login-section .btn-link:hover { text-decoration: underline; }
        #login-section .btn-success { background-color: var(--success-color); border: none; }
        #login-section .btn-danger { background-color: var(--danger-color); border: none; }
        #login-section .form-divider { text-align: center; margin: 20px 0; position: relative; color: var(--text-secondary); }
        #login-section .form-divider::before, #login-section .form-divider::after { content: ""; position: absolute; top: 50%; width: 40%; height: 1px; background-color: var(--border-color); }
        #login-section .form-divider::before { left: 0; } #login-section .form-divider::after { right: 0; }
        #login-section .form-divider span { background-color: var(--card-bg); padding: 0 10px; position: relative; z-index: 1; font-size: 0.8rem; font-weight: 500; }
        #login-section .card-title { color: var(--text-primary); } #googleSignInBtnMainEl { display: none; }
        .modal-content { background-color: var(--secondary-bg); color: var(--text-primary); border: 1px solid var(--border-color); }
        .modal-header { border-bottom-color: var(--border-color); } .modal-footer { border-top-color: var(--border-color); }
        .btn-close-white { filter: invert(1) grayscale(100%) brightness(200%); }
        .modal-body .phonepe-number { color: var(--warning-color); font-weight: bold; user-select: text; }
        #matchDetailsModalBodyEl pre { background-color: var(--primary-bg); padding: 10px; border-radius: 5px; border: 1px solid var(--border-color); color: var(--text-secondary); font-size: 0.85rem; white-space: pre-wrap; word-wrap: break-word; }
        #policyModalBodyEl { line-height: 1.6; font-size: 0.95rem; white-space: pre-wrap; }
        #idPasswordModalEl .copy-btn { padding: 2px 6px; font-size: 0.8rem; margin-left: 8px; vertical-align: middle; }
        #policyModalBodyEl .copy-btn, #policyModalBodyEl #shareReferralBtn { padding: 4px 10px; font-size: 0.9rem; }
        #policyModalBodyEl #shareReferralBtn i, #policyModalBodyEl .copy-btn i { margin-right: 5px; }
        #securityWarning { background-color: var(--danger-color); color: white; padding: 10px 15px; text-align: center; font-size: 0.9rem; position: sticky; top: 60px; z-index: 999; border-bottom: 1px solid #a51d1d; }
        #securityWarning a { color: #ffdddd; text-decoration: underline; }
        #securityWarning button { background: none; border: 1px solid white; color: white; padding: 2px 8px; margin-left: 15px; font-size: 0.8rem; border-radius: 4px; cursor: pointer; }
        .nav-tabs .nav-link { background-color: transparent; border: 1px solid var(--border-color); border-bottom: none; color: var(--text-secondary); margin-bottom: -1px; }
        .nav-tabs .nav-link.active { background-color: var(--secondary-bg); color: var(--accent-color); border-color: var(--border-color); border-bottom-color: var(--secondary-bg); font-weight: 600; }
        .tab-content { background-color: var(--secondary-bg); padding: 15px; border: 1px solid var(--border-color); border-top: none; border-radius: 0 0 10px 10px; }
        #edit-profile-section { max-width: 500px; margin: auto; }
        .avatar-preview { width: 100px; height: 100px; border-radius: 50%; object-fit: cover; display: block; margin: 0 auto 20px; border: 3px solid var(--border-color); }
        #toast-message { position: fixed; bottom: -100px; left: 50%; transform: translateX(-50%); background-color: #333; color: white; padding: 12px 25px; border-radius: 8px; z-index: 1055; transition: bottom 0.5s ease-in-out; font-size: 0.95rem; box-shadow: 0 4px 15px rgba(0,0,0,0.2); }
        #toast-message.show { bottom: 80px; }
        body.light-mode { --primary-bg: #F0F2F5; --secondary-bg: #FFFFFF; --card-bg: #FFFFFF; --text-primary: #1C1E21; --text-secondary: #65676B; --border-color: #E0E0E0; --bottom-nav-bg: #FFFFFF; }
        body.light-mode .app-header, body.light-mode .bottom-nav { background-color: var(--secondary-bg); border-color: var(--border-color); box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08); }
        body.light-mode .header-back-button, body.light-mode .notification-icon, body.light-mode .header-game-title { color: var(--text-primary); }
        body.light-mode .form-control { background-color: #F0F2F5; color: var(--text-primary); border-color: #CCD0D5; }
        body.light-mode .form-control:focus { background-color: #FFFFFF; }
        body.light-mode .form-control::placeholder { color: var(--text-secondary); }
        body.light-mode .nav-item { color: var(--text-secondary); }
        body.light-mode .nav-item.active { color: #1877F2;  background-color: rgba(24, 119, 242, 0.1); }
        body.light-mode .tournament-card-tags span { background-color: var(--primary-bg); }
        body.light-mode .profile-links .form-switch .form-check-input { background-color: #BCC0C4; border-color: #BCC0C4; }
        body.light-mode .modal-content { background-color: var(--secondary-bg);  color: var(--text-primary); }
        body.light-mode .btn-close-white { filter: none; }
        body.light-mode .nav-tabs .nav-link.active { background-color: var(--secondary-bg); }
        body.light-mode .tab-content { background-color: var(--secondary-bg); }
        #help-center-container { display: none; flex-direction: column; height: calc(100vh - 80px - 65px); }
        .chat-messages-container { flex-grow: 1; overflow-y: auto; padding: 10px; display: flex; flex-direction: column; }
        .chat-message { max-width: 80%; width: fit-content; padding: 10px 15px; border-radius: 18px; margin-bottom: 8px; line-height: 1.4; word-wrap: break-word; }
        .chat-message.sent { align-self: flex-end; background-color: var(--accent-color); color: white; font-weight: 500; border-bottom-right-radius: 4px; margin-left: auto; }
        .chat-message.received { align-self: flex-start; background-color: var(--secondary-bg); color: var(--text-primary); border: 1px solid var(--border-color); border-bottom-left-radius: 4px; }
        .chat-input-area { display: flex; align-items: center; padding: 10px 0; border-top: 1px solid var(--border-color); }
        .chat-input-area input { flex-grow: 1; border-radius: 20px; border: 1px solid var(--border-color); background-color: var(--primary-bg); color: var(--text-primary); padding: 10px 15px; margin-right: 8px; }
        .chat-input-area input:focus { border-color: var(--accent-color); box-shadow: none; }
        .chat-input-area button { width: 40px; height: 40px; border-radius: 50%; background: var(--accent-gradient); color: white; border: none; font-size: 1.2rem; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
        body.light-mode .chat-message.received { background-color: #E9EBEE; color: var(--text-primary); border: none; }
        body.light-mode .chat-input-area { border-top: 1px solid var(--border-color); }
        body.light-mode .chat-input-area input { background-color: #F0F2F5; }
        
        .chat-sender-label { font-size: 0.75rem; font-weight: 600; margin-bottom: 5px; color: var(--accent-color); opacity: 0.9; }
        .chat-sender-label i { margin-right: 4px; }
        body.light-mode .chat-sender-label { color: #1877F2; }

        #joinTournamentModalEl .seat-selection-container { display: flex; flex-wrap: wrap; gap: 8px; max-height: 250px; overflow-y: auto; padding: 10px; background-color: var(--primary-bg); border-radius: 8px; border: 1px solid var(--border-color); }
        #joinTournamentModalEl .seat, #joinTournamentModalEl .seat-group { border: 1px solid var(--border-color); background-color: var(--secondary-bg); transition: background-color 0.2s, border-color 0.2s; }
        #joinTournamentModalEl .seat { aspect-ratio: 1 / 1; width: 45px; display: flex; align-items: center; justify-content: center; border-radius: 6px; font-size: 0.8rem; font-weight: 600; cursor: pointer; color: var(--text-primary); }
        #joinTournamentModalEl .seat.selected { background-color: var(--accent-color); color: #FFFFFF; border-color: var(--accent-color); }
        #joinTournamentModalEl .seat.occupied { background-color: var(--danger-color); opacity: 0.6; cursor: not-allowed; border-color: var(--danger-color); }
        #joinTournamentModalEl .seat:not(.occupied):hover { background-color: #2c2c2c; }
        #joinTournamentModalEl .seat-group { display: flex; align-items: center; padding: 5px; border-radius: 8px; gap: 5px; cursor: pointer; }
        #joinTournamentModalEl .seat-group.selected { border-color: var(--accent-color); box-shadow: 0 0 5px rgba(0, 168, 255, 0.5); }
        #joinTournamentModalEl .seat-group.occupied { cursor: not-allowed; opacity: 0.7; }
        #joinTournamentModalEl .seat-group:not(.occupied):hover { background-color: #2c2c2c; }
        #joinTournamentModalEl .seat-group .group-number { font-weight: 700; color: var(--text-secondary); font-size: 0.9rem; padding: 0 5px; }
        #joinTournamentModalEl .seat-group .seat { width: 35px; height: 35px; cursor: inherit; }
        #withdrawalSuccessModal .modal-content, #joinSuccessModal .modal-content { background-color: #FFFFFF; border-radius: 20px; box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1); border: none; text-align: center; padding: 30px; }
        #withdrawalSuccessModal .modal-body, #joinSuccessModal .modal-body { padding: 0; }
        #withdrawalSuccessModal .success-icon, #joinSuccessModal .success-icon { font-size: 60px; width: 100px; height: 100px; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; margin-bottom: 20px; }
        #withdrawalSuccessModal .success-icon { color: #28a745; background: linear-gradient(135deg, #d4edda, #c3e6cb); }
        #withdrawalSuccessModal h4, #joinSuccessModal h4 { font-weight: 700; color: #333; margin-bottom: 15px; }
        #withdrawalSuccessModal p, #joinSuccessModal p { color: #6c757d; font-size: 0.95rem; line-height: 1.6; margin-bottom: 25px; }
        #withdrawalSuccessModal .btn-confirm-ok, #joinSuccessModal .btn-confirm-ok { border: none; border-radius: 10px; color: white; font-weight: 600; padding: 12px 30px; transition: all 0.3s ease; width: 100%; }
        #withdrawalSuccessModal .btn-confirm-ok { background: linear-gradient(45deg, #28a745, #218838); }
        #withdrawalSuccessModal .btn-confirm-ok:hover { transform: translateY(-2px); box-shadow: 0 4px 15px rgba(40, 167, 69, 0.3); }
        body.light-mode #withdrawalSuccessModal .modal-content, body.light-mode #joinSuccessModal .modal-content { background-color: #FFFFFF; }
        body.dark-mode #withdrawalSuccessModal .modal-content, body.dark-mode #joinSuccessModal .modal-content { background-color: var(--secondary-bg); }
        body.dark-mode #withdrawalSuccessModal h4, body.dark-mode #joinSuccessModal h4 { color: var(--text-primary); }
        body.dark-mode #withdrawalSuccessModal p, body.dark-mode #joinSuccessModal p { color: var(--text-secondary); }
        .status-badge { font-size: 0.75rem; font-weight: 600; padding: 4px 8px; border-radius: 6px; }
        .status-pending { background-color: var(--warning-color); color: var(--primary-bg); }
        .status-successful { background-color: var(--success-color); color: var(--text-primary); }
        .status-rejected { background-color: var(--danger-color); color: var(--text-primary); }
        .txn-id { font-size: 0.8rem; color: var(--text-secondary); margin-top: 5px; word-break: break-all; }
        .txn-id strong { color: var(--text-primary); }
        @keyframes ticker { 0% { transform: translateX(0%); } 100% { transform: translateX(-100%); } }

        #splash-screen { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: #000; z-index: 10001; display: flex; align-items: center; justify-content: center; overflow: hidden; transition: opacity 0.8s ease-out 0.5s, transform 0.8s ease-out 0.5s; perspective: 1200px; }
        #splash-screen.hide { opacity: 0; transform: scale(1.5); }
        .splash-background { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: radial-gradient(ellipse at 50% 100%, rgba(0, 119, 182, 0.7), transparent 70%), radial-gradient(ellipse at 50% 0%, rgba(0, 168, 255, 0.4), transparent 80%); animation: bg-pulse 6s infinite ease-in-out; }
        @keyframes bg-pulse { 50% { background: radial-gradient(ellipse at 50% 100%, rgba(0, 168, 255, 0.7), transparent 70%), radial-gradient(ellipse at 50% 0%, rgba(0, 119, 182, 0.4), transparent 80%); } }
        .splash-content { position: relative; text-align: center; transform-style: preserve-3d; animation: content-enter 1.2s cubic-bezier(0.23, 1, 0.32, 1) 0.3s forwards; opacity: 0; transform: scale(0.8); width: 100%; }
        @keyframes content-enter { from { opacity: 0; transform: scale(0.8) rotateX(-20deg); } to { opacity: 1; transform: scale(1) rotateX(0deg); } }
        .splash-title { font-family: 'Orbitron', sans-serif; font-size: 13vw; font-weight: 900; color: transparent; background-image: linear-gradient(135deg, #FFFFFF 0%, #00A8FF 50%, #0077B6 100%); -webkit-background-clip: text; background-clip: text; text-transform: uppercase; letter-spacing: 1px; position: relative; text-shadow: 0 0 10px rgba(0, 168, 255, 0.5), 0 0 20px rgba(0, 168, 255, 0.5), 0 0 40px rgba(0, 168, 255, 0.6); transform: translateZ(50px); padding: 0 10px; margin-bottom: 20px; }
        .splash-title::after { content: ''; position: absolute; top: 50%; left: -10%; width: 150%; height: 4px; background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.7), transparent); transform: translateY(-50%) skewX(-40deg) rotate(5deg); filter: blur(2px); opacity: 0; animation: lens-flare 2.5s ease-in-out 1.5s forwards; }
        @keyframes lens-flare { 0% { left: -50%; opacity: 0; } 30% { opacity: 1; } 80% { left: 100%; opacity: 1; } 100% { left: 100%; opacity: 0; } }
        .splash-cup { font-size: 45vw; display: inline-block; margin: -5vh 0; position: relative; color: transparent; background-image: linear-gradient(135deg, #FFFFFF 10%, #00A8FF 50%, #0077B6 90%); -webkit-background-clip: text; background-clip: text; filter: drop-shadow(0 0 15px rgba(0, 168, 255, 0.6)) drop-shadow(0 0 35px rgba(0, 119, 182, 0.5)); animation: cup-float 6s ease-in-out infinite; transform: translateZ(-20px); }
        @keyframes cup-float { 0%, 100% { transform: translateY(0) rotateY(-8deg) translateZ(-20px) scale(1); } 50% { transform: translateY(-20px) rotateY(8deg) translateZ(-20px) scale(1.05); } }
        .splash-welcome { font-family: 'Poppins', sans-serif; font-size: 6vw; font-weight: 600; color: #FFFFFF; text-shadow: 0 0 10px rgba(255, 255, 255, 0.6), 0 0 20px rgba(0, 168, 255, 0.7); margin-top: -5vh; position: relative; transform: translateZ(80px); opacity: 0; animation: welcome-fade-in 1s ease 2s forwards; }
        @keyframes welcome-fade-in { to { opacity: 1; } }
        .cash-container { position: absolute; top: 0; left: 0; width: 100%; height: 100%; transform-style: preserve-3d; pointer-events: none; }
        .cash-float { position: absolute; background: rgba(30, 30, 30, 0.7); color: #00A8FF; padding: 4px 12px; border-radius: 8px; border: 1px solid rgba(0, 168, 255, 0.5); font-weight: 700; font-size: 3.5vw; opacity: 0; animation: float-up 5s ease-out forwards infinite; backdrop-filter: blur(3px); }
        .cf-1 { top: 35%; left: 5%; animation-delay: 1s; } .cf-2 { top: 45%; right: 2%; animation-delay: 2.2s; } .cf-3 { top: 65%; left: 15%; animation-delay: 1.6s; }
        @keyframes float-up { 0% { transform: translateY(0) scale(0.7) rotateZ(-5deg); opacity: 0; } 20% { opacity: 1; } 90% { opacity: 1; } 100% { transform: translateY(-120px) scale(1.1) rotateZ(10deg); opacity: 0; } }
        .money-note { position: absolute; width: 15vw; height: 7vw; background: linear-gradient(45deg, #388E3C, #81C784); border-radius: 4px; opacity: 0; display: flex; align-items: center; justify-content: center; color: #FFFDE4; font-size: 4vw; font-weight: bold; box-shadow: 0 2px 10px rgba(0,0,0,0.5); animation: fly-by 5s linear forwards infinite; }
        .mn-1 { top: 15%; left: -20%; animation-delay: 0.5s; } .mn-2 { top: 75%; left: -20%; animation-delay: 2.1s; } .mn-3 { top: 25%; left: 120%; animation-delay: 1.5s; } .mn-4 { top: 85%; left: 120%; animation-delay: 3s; }
        @keyframes fly-by { 0% { transform: translateX(0) translateY(0) rotateZ(0deg) rotateY(0deg) scale(0.8); opacity: 0; } 15% { opacity: 0.9; } 85% { opacity: 0.9; } 100% { transform: translateX(calc(var(--dir, -1) * 140vw)) translateY(calc(var(--sway) * 50px)) rotateZ(720deg) rotateY(360deg) scale(1.1); opacity: 0; } }

        .game-category-tabs { display: flex; gap: 10px; margin-bottom: 20px; overflow-x: auto; padding-bottom: 5px; -ms-overflow-style: none; scrollbar-width: none; }
        .game-category-tabs::-webkit-scrollbar { display: none; }
        .category-tab-item { flex-shrink: 0; background-color: var(--secondary-bg); color: var(--text-secondary); border: 1px solid var(--border-color); padding: 8px 15px; border-radius: 20px; font-size: 0.9rem; font-weight: 600; cursor: pointer; transition: all 0.2s ease-in-out; }
        .category-tab-item:hover { background-color: #2c2c2c; color: var(--text-primary); }
        .category-tab-item.active { background: var(--accent-gradient); color: white; border-color: transparent; box-shadow: 0 2px 10px rgba(0, 168, 255, 0.3); }

        .password-wrapper { position: relative; }
        .toggle-password { position: absolute; top: 50%; right: 15px; transform: translateY(-50%); cursor: pointer; color: var(--text-secondary); }

  </style>
</head>

<body>
    
    <!-- ================================== -->
    <!-- Cinematic Intro Animation -->
    <!-- ================================== -->
    <div id="splash-screen">
        <div class="splash-background"></div>
        <div class="cash-container">
            <div class="cash-float cf-1">₹300 Won</div>
            <div class="cash-float cf-2">₹1000 Won</div>
            <div class="cash-float cf-3">₹500 Won</div>
            <div class="money-note mn-1" style="--dir: 1; --sway: 1;">₹</div>
            <div class="money-note mn-2" style="--dir: 1; --sway: -1;">₹</div>
            <div class="money-note mn-3" style="--dir: -1; --sway: -1;">₹</div>
            <div class="money-note mn-4" style="--dir: -1; --sway: 1;">₹</div>
        </div>
        <div class="splash-content">
             <h1 class="splash-title">2026</h1> 

            <h1 class="splash-title">RK Club Tournament 👑</h1>  
            <i class="fa-solid fa-trophy splash-cup"></i>
            <p class="splash-welcome">Welcome, <span id="splash-username">Player</span></p>
        </div>
    </div>


     <!-- Firebase Security Rules Warning -->
    <div id="securityWarning" style="display: none;">
        <i class="fa-solid fa-triangle-exclamation"></i> <strong>Security Alert:</strong> Your database rules are insecure (public). Anyone can read/write data.
        <a href="https://firebase.google.com/docs/database/security" target="_blank" rel="noopener noreferrer">Learn how to secure rules.</a>
        <button onclick="this.parentElement.style.display='none'">Dismiss</button>
    </div>

    <!-- Header -->
    <header class="app-header">
        <div class="header-left">
            <button class="header-back-button" id="headerBackBtnEl"><i class="fa-solid fa-arrow-left"></i></button>
            <img src="https://via.placeholder.com/40/FFFFFF/0F172A?text=G" alt="Logo" class="header-logo" id="appLogoEl">
            <div class="header-title" id="headerTitleContainerEl">
                Welcome
                <span id="headerUserGreetingEl">Guest</span>
            </div>
            <div class="header-game-title" id="headerGameTitleEl">Game Title</div>
        </div>
        <div class="header-right">
            <button class="notification-icon" id="notificationBtnEl">
                <i class="fa-solid fa-bell"></i>
                <span class="notification-badge" style="display: none;"></span>
            </button>
            <button class="wallet-chip" id="headerWalletChipEl" style="display: none;">
                <i class="fa-solid fa-wallet"></i> ₹<span id="headerChipBalanceEl">0</span>
            </button>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="main-content">
        <div id="globalLoaderEl"> <div class="spinner-border" role="status"><span class="visually-hidden">Loading...</span></div> </div>

        <!-- Login Section -->
        <section id="login-section" class="section">
             <div class="container" style="max-width: 450px;">
                <div class="card shadow-sm custom-card">
                    <div class="card-body p-4">
                        <!-- Common Login Form -->
                        <form id="loginForm">
                            <h2 class="card-title text-center mb-4">Login</h2>
                            <div class="mb-3">
                                <label for="loginIdentifierInputEl" class="form-label">Email or Phone Number</label>
                                <input type="text" class="form-control" id="loginIdentifierInputEl" placeholder="Enter your email or phone number" required>
                            </div>
                            <div class="mb-3">
                                <label for="loginPasswordInputEl" class="form-label">Password</label>
                                <div class="password-wrapper">
                                    <input type="password" class="form-control" id="loginPasswordInputEl" placeholder="Password" required>
                                    <i class="bi bi-eye-slash toggle-password"></i>
                                </div>
                            </div>
                            <div id="loginStatusMessageEl" class="alert mt-3" style="display: none;"></div>
                            <div class="d-grid gap-2">
                                <button type="button" class="btn btn-custom btn-custom-primary" id="loginBtnEl">Login</button>
                            </div>
                            <div class="d-flex justify-content-between mt-3">
                                <a href="#" id="forgotPasswordLinkEl" class="btn-custom-link btn-sm p-0" style="color: var(--text-secondary);">Forgot Password?</a>
                                <button type="button" class="btn-custom-link btn-sm p-0" id="showSignupToggleBtnEl">Need an account? Sign Up</button>
                            </div>
                            
                            <div class="form-divider mt-4"><span>OR</span></div>
                            <div class="d-grid">
                                <button type="button" class="btn btn-custom btn-custom-secondary" id="googleSignInBtn">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-google me-2" viewBox="0 0 16 16">
                                        <path d="M15.545 6.558a9.42 9.42 0 0 1 .139 1.626c0 2.434-.87 4.492-2.384 5.885h.002C11.978 15.292 10.158 16 8 16A8 8 0 1 1 8 0a7.689 7.689 0 0 1 5.352 2.082l-2.284 2.284A4.347 4.347 0 0 0 8 3.166c-2.087 0-3.86 1.408-4.492 3.25C2.898 8.128 4.783 10 8 10c1.283 0 2.388-.328 3.203-.924l2.344 2.344A7.984 7.984 0 0 1 15.545 6.558z"/>
                                    </svg>
                                    Sign in with Google
                                </button>
                            </div>

                        </form>

                  <!-- Download App Button -->
<div class="text-center mt-3">
    <p class="text-secondary small mb-2">For better experience</p>
    <a href="https://rkclubtournament.42web.io/" class="btn btn-outline-success w-100" download>
        <i class="fa-brands fa-android"></i> Download Android App
    </a>
</div>

download="https://rkclubtournament.42web.io/`;
                        <!-- Signup Form -->
                        <form id="signupForm" style="display: none;">
                            <h2 class="card-title text-center mb-4">Sign Up</h2>
                            <div class="mb-3"> <label for="signupNameInputEl" class="form-label">Full Name</label> <input type="text" class="form-control" id="signupNameInputEl" placeholder="Enter your full name" required> </div>
                            <div class="mb-3"> <label for="signupEmailInputEl" class="form-label">Email</label> <input type="email" class="form-control" id="signupEmailInputEl" placeholder="name@example.com" required> </div>
                            <div class="mb-3"> <label for="signupPhoneInputEl" class="form-label">Phone Number</label> <input type="tel" class="form-control" id="signupPhoneInputEl" placeholder="Enter 10-digit number" required pattern="[6-9][0-9]{9}" title="Please enter a valid 10-digit Indian mobile number."> </div>
                            <div class="mb-3">
                                <label for="signupPasswordInputEl" class="form-label">Password (min 6 chars)</label>
                                <div class="password-wrapper">
                                    <input type="password" class="form-control" id="signupPasswordInputEl" placeholder="Password" required minlength="6">
                                    <i class="bi bi-eye-slash toggle-password"></i>
                                </div>
                            </div>
                            <div class="mb-3">
                                <label for="signupConfirmPasswordInputEl" class="form-label">Confirm Password</label>
                                <div class="password-wrapper">
                                    <input type="password" class="form-control" id="signupConfirmPasswordInputEl" placeholder="Confirm Password" required>
                                    <i class="bi bi-eye-slash toggle-password"></i>
                                </div>
                            </div>
                            <div class="mb-3">
                                <label for="signupReferralCodeInputEl" class="form-label">Referral Code (Optional)</label>
                                <input type="text" class="form-control" id="signupReferralCodeInputEl" placeholder="Enter referral code">
                            </div>
                            <div id="signupStatusMessageEl" class="alert mt-3" style="display: none;"></div>
                            <div class="d-grid gap-2"> <button type="button" class="btn btn-custom btn-custom-accent" id="signupBtnEl">Sign Up with Email</button> </div>
                            
                            <div class="form-divider mt-3"><span>OR</span></div>
                            <div class="d-grid">
                                <button type="button" class="btn btn-custom btn-custom-secondary" id="googleSignInBtnSignup">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" class="bi bi-google me-2" viewBox="0 0 16 16">
                                        <path d="M15.545 6.558a9.42 9.42 0 0 1 .139 1.626c0 2.434-.87 4.492-2.384 5.885h.002C11.978 15.292 10.158 16 8 16A8 8 0 1 1 8 0a7.689 7.689 0 0 1 5.352 2.082l-2.284 2.284A4.347 4.347 0 0 0 8 3.166c-2.087 0-3.86 1.408-4.492 3.25C2.898 8.128 4.783 10 8 10c1.283 0 2.388-.328 3.203-.924l2.344 2.344A7.984 7.984 0 0 1 15.545 6.558z"/>
                                    </svg>
                                    Sign up with Google
                                </button>
                            </div>
                            
                            <div class="text-center mt-3">
                                <button type="button" class="btn-custom-link btn-sm p-0" id="showLoginToggleBtnEl">Already have an account? Login</button>
                            </div>
                        </form>

                        <!-- Forgot Password Form -->
                         <form id="forgotPasswordForm" style="display: none;">
                            <h2 class="card-title text-center mb-4">Reset Password</h2>
                             <div class="mb-3">
                                <label for="forgotEmailInputEl" class="form-label">Enter Your Registered Email</label>
                                <input type="email" class="form-control" id="forgotEmailInputEl" placeholder="Your registered email" required>
                            </div>
                            <div class="d-grid gap-2">
                                <button type="button" class="btn btn-custom btn-custom-primary" id="sendResetLinkBtnEl">Send Reset Link</button>
                            </div>
                            <div id="forgotStatusMessageEl" class="alert mt-3" style="display: none;"></div>
                            <div class="d-grid gap-2 mt-3">
                                <button type="button" class="btn-custom-link btn-sm p-0 text-center d-block" id="backToLoginBtnEl">Back to Login</button>
                            </div>
                        </form>

                    </div>
                </div>
            </div>
        </section>

        <!-- Home Section -->
        <section id="home-section" class="section">
            <!-- Promotion Slider -->
            <div class="swiper-container" id="promotionSliderEl">
                <div class="swiper-wrapper placeholder-glow">
                    <div class="swiper-slide"><span class="placeholder" style="display: block; width: 100%; height: 100%; border-radius: 10px;"></span></div>
                 </div>
                 <div class="swiper-pagination"></div>
            </div>

            <!-- =============== MODIFIED ADVERTISEMENT SECTION =============== -->
            <div class="swiper-container" id="homePageAdContainer" style="margin-top: 25px; border-radius: 10px; overflow: hidden; display: none;">
                <div class="swiper-wrapper">
                    <!-- Ads will be loaded here from Firebase in real-time -->
                </div>
            </div>
            <!-- ======================================================= -->

            <!-- NEW: Game Category Tabs for Home -->
            <h2 class="section-title">Categories</h2>
            <div id="homeCategoryTabs" class="game-category-tabs"></div>

            <!-- Esport Games -->
            <h2 class="section-title">Esport Games</h2>
            <div class="row g-3 mb-4 placeholder-glow" id="gamesListEl">
                <!-- Placeholder Game Cards -->
                <div class="col-12"> <div class="game-card custom-card"><span class="placeholder d-block" style="height: 0; padding-bottom: 56.25%;"></span><span class="placeholder d-block mt-2 col-8 mx-auto" style="height: 20px;"></span></div> </div>
                <div class="col-12"> <div class="game-card custom-card"><span class="placeholder d-block" style="height: 0; padding-bottom: 56.25%;"></span><span class="placeholder d-block mt-2 col-8 mx-auto" style="height: 20px;"></span></div> </div>
            </div>

            <!-- My Contests -->
            <h2 class="section-title">My Contests</h2>
            <div id="myContestsListEl" class="placeholder-glow">
                 <!-- Placeholder Contest Card -->
                <div class="tournament-card placeholder-glow mb-3"> <span class="placeholder col-6" style="height: 18px;"></span> <span class="placeholder col-12 mt-2" style="height: 24px;"></span> <span class="placeholder col-10 mt-2" style="height: 16px;"></span> <div class="d-flex justify-content-between mt-3"> <span class="placeholder col-4" style="height: 30px; border-radius: 6px;"></span> <span class="placeholder col-4" style="height: 30px; border-radius: 6px;"></span> </div> </div>
                <p id="noContestsMessageEl" class="text-secondary text-center" style="display: none;">You haven't joined any contests yet.</p>
            </div>
            
        </section>

        <!-- NEW: Matches Section (to show all games) -->
        <section id="matches-section" class="section">
            <h2 class="section-title">Choose a Game</h2>
            <!-- NEW: Game Category Tabs for Matches -->
            <div id="matchesCategoryTabs" class="game-category-tabs"></div>

            <div class="row g-3 mb-4 placeholder-glow" id="allGamesListEl">
                <!-- Placeholder Game Cards -->
                <div class="col-12"> <div class="game-card custom-card"><span class="placeholder d-block" style="height: 0; padding-bottom: 56.25%;"></span><span class="placeholder d-block mt-2 col-8 mx-auto" style="height: 20px;"></span></div> </div> <div class="col-12"> <div class="game-card custom-card"><span class="placeholder d-block" style="height: 0; padding-bottom: 56.25%;"></span><span class="placeholder d-block mt-2 col-8 mx-auto" style="height: 20px;"></span></div> </div>
            </div>
        </section>


        <!-- Tournaments Section (For a specific game, now hidden until a game is clicked) -->
        <section id="tournaments-section" class="section">
            <div class="tournament-tabs"> <button class="tab-item active" data-status="upcoming"><i class="fa-solid fa-calendar-days"></i> Upcoming</button> <button class="tab-item" data-status="ongoing"><i class="fa-solid fa-circle-play"></i> Ongoing</button> <button class="tab-item" data-status="completed"><i class="fa-solid fa-trophy"></i> Results</button> </div>
            <div id="tournamentsListContainerEl" class="mt-3 placeholder-glow"> <div class="tournament-card placeholder-glow mb-3"> <span class="placeholder col-6" style="height: 18px;"></span> <span class="placeholder col-12 mt-2" style="height: 24px;"></span> <span class="placeholder col-10 mt-2" style="height: 16px;"></span> <div class="d-flex justify-content-between mt-3"> <span class="placeholder col-4" style="height: 30px; border-radius: 6px;"></span> <span class="placeholder col-4" style="height: 30px; border-radius: 6px;"></span> </div> </div> </div>
            <p id="noTournamentsMessageEl" class="text-secondary text-center mt-4" style="display: none;">No tournaments found.</p>
        </section>

        <!-- Wallet Section -->
        <section id="wallet-section" class="section">
            <div class="wallet-card custom-card">
                <h2 class="section-title mb-4">Wallet</h2>
                <div class="balance-item placeholder-glow"> <span class="balance-item-label">Total Balance</span> <span class="balance-item-value" id="walletTotalBalanceEl"><span class="placeholder col-3"></span></span> <div class="balance-item-action"> <button class="btn-custom-link" id="allTransactionsBtnEl">History <i class="fa-solid fa-chevron-right"></i></button> </div> </div>
                <div class="balance-item placeholder-glow"> <span class="balance-item-label">Winning Cash</span> <span class="balance-item-value" id="walletWinningCashEl"><span class="placeholder col-3"></span></span> <div class="balance-item-action"> <button class="btn-withdraw" id="withdrawBtnEl">Withdraw</button> </div> </div>
                <div class="balance-item placeholder-glow"> <span class="balance-item-label">Bonus Cash</span> <span class="balance-item-value" id="walletBonusCashEl"><span class="placeholder col-3"></span></span> <div class="balance-item-action" style="min-width: 100px;"></div> </div>
                <button class="btn btn-custom btn-custom-secondary w-100 mt-4" id="addAmountWalletBtnEl"> <i class="fa-solid fa-plus-circle me-2"></i>Add Amount </button>
            </div>
            <h3 class="section-title mt-4">Recent Transactions</h3>
            <div id="recentTransactionsListEl" class="placeholder-glow"> <div class="custom-card p-2 mb-2 placeholder-glow"> <div class="d-flex justify-content-between"> <span class="placeholder col-5" style="height: 16px;"></span> <span class="placeholder col-3" style="height: 16px;"></span> </div> <div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div> </div> <p class="text-secondary text-center mt-3" id="noTransactionsMessageEl" style="display: none;">Loading transactions...</p> </div>
        </section>

        <!-- Transactions History Section -->
        <section id="transactions-section" class="section">
            <h2 class="section-title">History</h2>
            <ul class="nav nav-tabs nav-fill mb-3" id="historyTabs" role="tablist">
                <li class="nav-item" role="presentation">
                    <button class="nav-link active" id="all-transactions-tab" data-bs-toggle="tab" data-bs-target="#all-transactions-pane" type="button" role="tab">All Transactions</button>
                </li>
                <li class="nav-item" role="presentation">
                    <button class="nav-link" id="withdrawals-tab" data-bs-toggle="tab" data-bs-target="#withdrawals-pane" type="button" role="tab">Withdrawals</button>
                </li>
            </ul>

            <div class="tab-content" id="historyTabsContent">
                <div class="tab-pane fade show active" id="all-transactions-pane" role="tabpanel" tabindex="0">
                    <div id="fullTransactionsListEl" class="placeholder-glow">
                        <!-- Placeholder Transaction -->
                        <div class="custom-card p-2 mb-2 placeholder-glow">
                            <div class="d-flex justify-content-between">
                                <span class="placeholder col-5" style="height: 16px;"></span>
                                <span class="placeholder col-3" style="height: 16px;"></span>
                            </div>
                            <div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div>
                        </div>
                    </div>
                    <p id="noFullTransactionsMessageEl" class="text-secondary text-center mt-4" style="display: none;">No transactions found.</p>
                </div>
                <div class="tab-pane fade" id="withdrawals-pane" role="tabpanel" tabindex="0">
                    <div id="withdrawalHistoryListEl" class="placeholder-glow">
                        <!-- Placeholder Withdrawal -->
                        <div class="custom-card p-2 mb-2 placeholder-glow">
                            <div class="d-flex justify-content-between">
                                <span class="placeholder col-4" style="height: 20px;"></span>
                                <span class="placeholder col-3" style="height: 20px; border-radius: 6px;"></span>
                            </div>
                            <div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div>
                        </div>
                    </div>
                    <p id="noWithdrawalHistoryMessageEl" class="text-secondary text-center mt-4" style="display: none;">No withdrawal history found.</p>
                </div>
            </div>
        </section>

        
        <!-- Earnings Section -->
        <section id="earnings-section" class="section">
            <div id="earnings-main-view">
                <h2 class="section-title">Earnings</h2>
                <div class="custom-card text-center">
                    <i class="fa-solid fa-sack-dollar display-4 text-accent mb-3"></i>
                    <p class="text-secondary mb-4">Track your earnings from tournaments and referrals here.</p>
                    <div class="placeholder-glow">
                        <p>Total Earned: <strong id="earningsTotalEl"><span class="placeholder col-3"></span></strong></p>
                        <p>From Referrals: <strong id="earningsReferralEl"><span class="placeholder col-3"></span></strong></p>
                    </div>
                    <button class="btn btn-custom btn-custom-link mt-3" id="viewEarningsHistoryBtn">View History</button>
                </div>

                <!-- NEW: Top Earners Leaderboard -->
                <h3 class="section-title mt-4">Top Earners (All Time)</h3>
                <div id="topEarnersListEl" class="placeholder-glow">
                    <!-- Placeholder items -->
                    <div class="custom-card p-3 mb-2 placeholder-glow">
                        <div class="d-flex justify-content-between align-items-center">
                            <div class="d-flex align-items-center">
                                <span class="placeholder me-3" style="width: 40px; height: 40px; border-radius: 50%;"></span>
                                <div>
                                    <span class="placeholder col-5 d-block" style="height: 16px;"></span>
                                    <span class="placeholder col-8 d-block mt-1" style="height: 14px;"></span>
                                </div>
                            </div>
                            <span class="placeholder col-3" style="height: 20px;"></span>
                        </div>
                    </div>
                    <div class="custom-card p-3 mb-2 placeholder-glow">
                        <div class="d-flex justify-content-between align-items-center">
                            <div class="d-flex align-items-center">
                                <span class="placeholder me-3" style="width: 40px; height: 40px; border-radius: 50%;"></span>
                                <div>
                                    <span class="placeholder col-5 d-block" style="height: 16px;"></span>
                                    <span class="placeholder col-8 d-block mt-1" style="height: 14px;"></span>
                                </div>
                            </div>
                            <span class="placeholder col-3" style="height: 20px;"></span>
                        </div>
                    </div>
                </div>
                <p id="noTopEarnersMessageEl" class="text-secondary text-center mt-3" style="display: none;">No top earners data available yet.</p>

            </div>
        </section>

        <!-- Earnings History Section -->
        <section id="earnings-history-section" class="section">
            <h2 class="section-title">Earnings History</h2>
            <div id="fullEarningsListEl" class="placeholder-glow">
                <!-- Placeholder Earning Item -->
                <div class="custom-card p-2 mb-2 placeholder-glow">
                    <div class="d-flex justify-content-between">
                        <span class="placeholder col-5" style="height: 16px;"></span>
                        <span class="placeholder col-3" style="height: 16px;"></span>
                    </div>
                    <div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div>
                </div>
            </div>
            <p id="noFullEarningsMessageEl" class="text-secondary text-center mt-4" style="display: none;">No earnings history found.</p>
        </section>


        <!-- Profile Section -->
        <section id="profile-section" class="section">
            
            <!-- Main Profile View -->
            <div id="profile-view-container">
                <div class="profile-header-card placeholder-glow">
                    <img src="https://via.placeholder.com/70" alt="Avatar" class="profile-avatar" id="profileAvatarEl">
                    <h3 class="profile-name mt-2" id="profileNameEl"><span class="placeholder col-6"></span></h3>
                    <p class="profile-email" id="profileEmailEl"><span class="placeholder col-8"></span></p>
                    <div class="profile-stats w-100">
                        <div class="stat-item"><strong id="profileTotalMatchesEl"><span class="placeholder col-4"></span></strong><span>Matches Played</span></div>
                        <div class="stat-item"><strong id="profileWonMatchesEl"><span class="placeholder col-4"></span></strong><span>Matches Won</span></div>
                        <div class="stat-item"><strong id="profileTotalEarningsEl"><span class="placeholder col-4"></span></strong><span>Total Winnings</span></div>
                    </div>
                </div>

                <div class="profile-links">
                    <div class="list-group custom-card">
                       <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" id="editProfileBtn">
                            <span><i class="fa-solid fa-user-pen"></i> Edit Profile</span>
                            <i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" id="changePasswordBtnEl">
                            <span><i class="fa-solid fa-key"></i> Change Password</span>
                            <i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <label class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item">
                            <span><i class="fa-solid fa-bell"></i> Notifications</span>
                            <div class="form-check form-switch">
                                <input class="form-check-input" type="checkbox" role="switch" id="notificationSwitchEl" checked>
                            </div>
                        </label>
                        <label class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item">
                            <span><i class="fa-solid fa-circle-half-stroke"></i> Dark Mode</span>
                            <div class="form-check form-switch">
                                <input class="form-check-input" type="checkbox" role="switch" id="themeSwitchEl">
                            </div>
                        </label>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" data-policy="refer">
                            <span><i class="fa-solid fa-user-group"></i> Refer & Earn</span>
                            <i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" id="helpCenterBtn">
                            <span><i class="fa-solid fa-headset"></i> Help Center</span>
                            <i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" data-policy="privacy">
                            <span><i class="fa-solid fa-shield"></i> Privacy Policy</span><i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" data-policy="terms">
                            <span><i class="fa-solid fa-file-contract"></i> Terms and Conditions</span><i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" data-policy="refund">
                            <span><i class="fa-solid fa-arrows-rotate"></i> Refund and Cancellation</span><i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <a href="#" class="list-group-item list-group-item-action d-flex justify-content-between align-items-center interactive-list-item" data-policy="fairPlay">
                            <span><i class="fa-solid fa-award"></i> Fair Play Policy</span><i class="fa-solid fa-chevron-right"></i>
                        </a>
                        <button class="list-group-item list-group-item-action text-danger d-flex justify-content-between align-items-center interactive-list-item" id="logoutProfileBtnEl">
                            <span><i class="fa-solid fa-right-from-bracket"></i> Logout</span><span></span>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Edit Profile Form (Hidden by default) -->
            <div id="edit-profile-container" style="display: none;">
                 <div class="custom-card p-3">
                    <h3 class="text-center mb-4">Edit Profile</h3>
                    <form id="editProfileForm">
                        <img src="https://via.placeholder.com/100" alt="Avatar Preview" class="avatar-preview" id="avatarPreview">
                        <div class="mb-3">
                            <label for="logoInput" class="form-label">Change Profile Logo</label>
                            <input class="form-control" type="file" id="logoInput" accept="image/*">
                        </div>
                        <div class="mb-3">
                            <label for="nameInput" class="form-label">Name</label>
                            <input type="text" class="form-control" id="nameInput" placeholder="Your Name" required>
                        </div>
                        <div class="mb-3">
                            <label for="emailInput" class="form-label">Email (cannot be changed)</label>
                            <input type="email" class="form-control" id="emailInput" placeholder="your.email@example.com" disabled>
                        </div>
                        <div id="editProfileStatusMessageEl" class="alert mt-3" style="display: none;"></div>
                        <div class="d-grid gap-2">
                            <button type="submit" class="btn btn-custom btn-custom-primary">Save Changes</button>
                            <button type="button" class="btn btn-custom btn-custom-secondary" id="cancelEditBtn">Cancel</button>
                        </div>
                    </form>
                </div>
            </div>

            <!-- Help Center Chat View (Hidden by default) -->
            <div id="help-center-container">
                <div class="chat-messages-container" id="chatMessagesContainerEl">
                    <!-- Messages will be loaded here -->
                </div>
                <div class="chat-input-area">
                    <input type="text" id="chatMessageInputEl" class="form-control" placeholder="Type your message...">
                    <button id="chatSendBtnEl"><i class="fa-solid fa-paper-plane"></i></button>
                </div>
            </div>



<!-- Social Media Icons -->
<div class="text-center mt-4">
    <p class="mb-2" style="font-size: 14px; color: var(--text-secondary); letter-spacing: 1px;">
        — Follow us for updates and tournaments —
    </p>
    <div class="social-icons" style="display: flex; justify-content: center; gap: 30px; margin-bottom: 30px;">
        <a href="https://www.youtube.com/@RKClubTournament" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/512/1384/1384060.png" alt="YouTube" style="width: 40px; height: 40px; transition: 0.3s; filter: drop-shadow(0 0 10px #ff0000);">
        </a>
        <a href="https://t.me/+FSh0sY_5W78zYjZl" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" alt="Telegram" style="width: 40px; height: 40px; transition: 0.3s; filter: drop-shadow(0 0 10px #229ED9);">
        </a>
         <a href="https://chat.whatsapp.com/HaWROBq9W2fGKF82DtQkjl" target="_blank">
           <img src="https://cdn-icons-png.flaticon.com/512/733/733585.png" alt="WhatsApp" style="width: 40px; height: 40px; transition: 0.3s; filter: drop-shadow(0 0 10px #25D366);">
        </a>
        <a href="https://www.instagram.com/life_with_ayan_74?igsh=MTQwdzN3Zm8yNTRlOA==" target="_blank">
          <img src="https://cdn-icons-png.flaticon.com/512/1384/1384063.png" alt="Instagram" style="width: 40px; height: 40px; transition: 0.3s; filter: drop-shadow(0 0 10px #C13584);">
        </a>
    </div>
</div>




<!-- Cinematic Scrolling Footer -->
<footer style="
    position: fixed;
    bottom: 65px;
    left: 0;
    width: 100%;
    background: rgba(18, 18, 18, 0.85);
    border-top: 1px solid var(--border-color);
    overflow: hidden;
    z-index: 999;
    padding: 8px 0;
    backdrop-filter: blur(5px);
">
    <div style="
        display: inline-block;
        white-space: nowrap;
        padding-left: 100%;
        animation: ticker 25s linear infinite;
        font-family: 'Poppins', sans-serif;
        font-weight: 500;
        letter-spacing: 1px;
        font-size: 0.95rem;
        color: #eaeaea;
    ">
        
        <span style="margin-right: 80px;">
            ✨ <strong>Vision Crafted By:</strong> <span style="color:var(--accent-color);">RAKESH BISWA </span> 🛠️
        </span>

        <span style="margin-right: 80px;">
            🎯 <strong>100% save tournament app :</strong> 
            <span style="color:#ffffff;">Free fire 🔥</span>  |  
            <span style="color:#ffffff;">Tunament</span>  |  
            <span style="color:#ffffff;">WIN 100%</span>  | 
            <span style="color:#ffffff;"> play match</span> 🏆
        </span>

        <span style="margin-right: 80px;">
            🚀 <strong>Powered by the Force of:</strong> 
            <span style="color:var(--accent-color);"> Rakesh Biswas Ꭼ-ꮪꮲꭷꮢꭲꮪ </span> 🔥
        </span>
    </div>
</footer>

<!-- Smooth Ticker Animation -->
<style>
@keyframes ticker {
    0% { transform: translateX(0%); }
    100% { transform: translateX(-100%); }
}
</style>



        </section>

        <!-- MODAL FOR CHANGING PASSWORD (ADD THIS) -->
        <div class="modal fade" id="changePasswordModalEl" tabindex="-1">
            <div class="modal-dialog modal-dialog-centered">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title">Change Password</h5>
                        <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
                    </div>
                    <div class="modal-body">
                        <form id="changePasswordForm">
                            <div class="mb-3">
                                <label for="oldPasswordInputEl" class="form-label">Old Password</label>
                                <input type="password" class="form-control" id="oldPasswordInputEl" placeholder="Enter your current password" required>
                            </div>
                            <div class="mb-3">
                                <label for="newPasswordInputEl" class="form-label">New Password</label>
                                <input type="password" class="form-control" id="newPasswordInputEl" placeholder="Enter new password (min. 6 characters)" required>
                            </div>
                            <div class="mb-3">
                                <label for="confirmPasswordInputEl" class="form-label">Confirm New Password</label>
                                <input type="password" class="form-control" id="confirmPasswordInputEl" placeholder="Confirm your new password" required>
                            </div>
                            <div id="changePasswordStatusMessageEl" class="alert" style="display: none;"></div>
                            <div class="d-grid">
                                <button type="submit" class="btn btn-custom btn-custom-primary" id="updatePasswordBtnEl">Update Password</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </main>
    
    <!-- Toast Notification -->
    <div id="toast-message"></div>

    <!-- Modals -->
    <div class="modal fade" id="policyModalEl" tabindex="-1"><div class="modal-dialog modal-dialog-scrollable modal-lg"><div class="modal-content"><div class="modal-header"><h5 class="modal-title" id="policyModalTitleEl">Details</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div><div class="modal-body" id="policyModalBodyEl" style="min-height: 300px;"></div></div></div></div>
    <div class="modal fade" id="addAmountModalEl" tabindex="-1"><div class="modal-dialog modal-dialog-centered"><div class="modal-content"><div class="modal-header"><h5 class="modal-title"><i class="fa-solid fa-wallet me-2"></i> Add Amount</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div>
        <div class="modal-body">
            <p>Select an amount to add:</p>
            <div class="d-grid gap-2 mb-3" id="addAmountOptionsEl">
                <button class="btn btn-outline-warning" data-amount="20">₹20</button>
                <button class="btn btn-outline-warning" data-amount="50">₹50</button>
                <button class="btn btn-outline-warning" data-amount="100">₹100</button>
                <button class="btn btn-outline-warning" data-amount="200">₹200</button>
                <button class="btn btn-outline-warning" data-amount="500">₹500</button>
            </div>
            <div id="paymentInstructionsEl" style="display: none;">
                <hr>
                <p class="text-center">Pay the selected amount using the QR or UPI ID below:</p>

                <!---- QR Code Image Added Here -->
                <div class="text-center my-3">
                 <!----APNA PAYMENT KA QR LAGAO----// @CODEFREE GENIUS --->
                    <img src="https://i.ibb.co/4gg7gV57/Account-QRCode-Union-Bank-Of-India-1727-LIGHT-THEME.webp"
         alt="UPI QR Code"
" alt="Scan to Pay" style="width: 160px; height: auto; border-radius: 8px; border: 1px solid var(--border-color);">
                </div>
                
                <p class="text-center">
                     <!-----APNA UPI ID LAGAO---->
                    <strong>UPI ID:</strong> 
                    <span id="upiIdDisplay" class="phonepe-number">7477867457-4@ybl</span>
                    <button class="btn btn-sm btn-outline-secondary ms-2 copy-btn" data-target="#upiIdDisplay" title="Copy UPI ID">
                        <i class="fa-solid fa-clipboard"></i>
                    </button>
                </p>
                <p class="mt-3 small text-center">
                    <i class="fa-solid fa-triangle-exclamation text-warning"></i> 
                    <strong>IMPORTANT:</strong> After payment, send a screenshot to our WhatsApp number: 
                <!----APNA NUMBER ADD KARO // @CODEFREE GENIUS--->   
                     <strong>7477867457</strong>.
                </p>
                <p class="small text-center">Please wait for 30 minutes for the amount to be reflected in your wallet.</p>
            </div>
        </div>
    </div></div></div>
    <div class="modal fade" id="withdrawModalEl" tabindex="-1"><div class="modal-dialog modal-dialog-centered"><div class="modal-content"><div class="modal-header"><h5 class="modal-title"><i class="fa-solid fa-money-bill-transfer me-2"></i> Withdraw Funds</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div>
        <div class="modal-body">
            <p class="small text-secondary">Withdrawable balance: <strong class="text-light" id="withdrawModalBalanceEl">₹0.00</strong></p>
            
            <ul class="nav nav-tabs nav-fill mb-3" id="withdrawTabs" role="tablist">
                <li class="nav-item" role="presentation">
                    <button class="nav-link active" id="upi-tab" data-bs-toggle="tab" data-bs-target="#upi-tab-pane" type="button" role="tab" aria-controls="upi-tab-pane" aria-selected="true">UPI</button>
                </li>
                <li class="nav-item" role="presentation">
                    <button class="nav-link" id="bank-tab" data-bs-toggle="tab" data-bs-target="#bank-tab-pane" type="button" role="tab" aria-controls="bank-tab-pane" aria-selected="false">Bank Account</button>
                </li>
            </ul>

            <div class="tab-content" id="withdrawTabsContent">
                <div class="tab-pane fade show active" id="upi-tab-pane" role="tabpanel" aria-labelledby="upi-tab" tabindex="0">
                     <div class="mb-3">
                        <label for="withdrawUpiAmountInputEl" class="form-label">Amount (Min ₹<span id="minWithdrawAmountUpiEl">50</span>)</label>
                        <input type="number" class="form-control" id="withdrawUpiAmountInputEl" placeholder="Enter amount">
                    </div>
                    <div class="mb-3">
                        <label for="withdrawUpiIdInputEl" class="form-label">Your UPI ID</label>
                        <input type="text" class="form-control" id="withdrawUpiIdInputEl" placeholder="Enter your UPI ID">
                    </div>
                    <div class="d-grid">
                        <button type="button" class="btn btn-custom btn-custom-primary" id="submitUpiWithdrawBtnEl">Submit Request</button>
                    </div>
                </div>
                <div class="tab-pane fade" id="bank-tab-pane" role="tabpanel" aria-labelledby="bank-tab" tabindex="0">
                     <div class="mb-3">
                        <label for="withdrawBankAmountInputEl" class="form-label">Amount (Min ₹<span id="minWithdrawAmountBankEl">50</span>)</label>
                        <input type="number" class="form-control" id="withdrawBankAmountInputEl" placeholder="Enter amount">
                    </div>
                    <div class="mb-3">
                        <label for="withdrawBankNameInputEl" class="form-label">Account Holder Name</label>
                        <input type="text" class="form-control" id="withdrawBankNameInputEl" placeholder="Enter name as per bank">
                    </div>
                    <div class="mb-3">
                        <label for="withdrawBankAccountInputEl" class="form-label">Bank Account Number</label>
                        <input type="text" class="form-control" id="withdrawBankAccountInputEl" placeholder="Enter account number">
                    </div>
                    <div class="mb-3">
                        <label for="withdrawBankReAccountInputEl" class="form-label">Re-enter Account Number</label>
                        <input type="text" class="form-control" id="withdrawBankReAccountInputEl" placeholder="Confirm account number">
                    </div>
                    <div class="mb-3">
                        <label for="withdrawBankIfscInputEl" class="form-label">IFSC Code</label>
                        <input type="text" class="form-control" id="withdrawBankIfscInputEl" placeholder="Enter IFSC code">
                    </div>
                    <div class="d-grid">
                         <button type="button" class="btn btn-custom btn-custom-primary" id="submitBankWithdrawBtnEl">Submit Request</button>
                    </div>
                </div>
            </div>
            <div id="withdrawStatusMessageEl" class="alert mt-3" style="display: none;"></div>
        </div>
    </div></div></div>
    <div class="modal fade" id="matchDetailsModalEl" tabindex="-1"><div class="modal-dialog modal-dialog-centered modal-lg"><div class="modal-content"><div class="modal-header"><h5 class="modal-title" id="matchDetailsModalTitleEl">Match Details</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div><div class="modal-body" id="matchDetailsModalBodyEl"></div></div></div></div>
    <div class="modal fade" id="idPasswordModalEl" tabindex="-1"><div class="modal-dialog modal-dialog-centered"><div class="modal-content"><div class="modal-header"><h5 class="modal-title">Room ID & Password</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div><div class="modal-body text-center"><p class="small text-secondary">ID/Pass shown shortly before match start.</p><div class="my-3 p-3" style="background: var(--primary-bg); border-radius: 8px;"><p class="mb-1">Room ID:</p><h4 id="roomIdDisplayEl" class="text-accent referral-code placeholder-glow d-inline-block"><span class="placeholder col-6"></span></h4><button class="btn btn-sm btn-outline-warning ms-2 copy-btn" data-target="#roomIdDisplayEl" title="Copy Room ID"><i class="fa-solid fa-clipboard"></i></button></div><div class="my-3 p-3" style="background: var(--primary-bg); border-radius: 8px;"><p class="mb-1">Password:</p><h4 id="roomPasswordDisplayEl" class="text-accent referral-code placeholder-glow d-inline-block"><span class="placeholder col-6"></span></h4><button class="btn btn-sm btn-outline-warning ms-2 copy-btn" data-target="#roomPasswordDisplayEl" title="Copy Password"><i class="fa-solid fa-clipboard"></i></button></div><p class="small text-warning"><i class="fa-solid fa-triangle-exclamation"></i> Don't share ID/Password.</p></div></div></div></div>
    <div class="modal fade" id="notificationModalEl" tabindex="-1"><div class="modal-dialog modal-dialog-scrollable modal-lg"><div class="modal-content"><div class="modal-header"><h5 class="modal-title" id="notificationModalTitleEl">Notifications</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div><div class="modal-body" id="notificationModalBodyEl" style="min-height: 300px;"></div></div></div></div>

    <!-- Join Tournament Modal -->
    <div class="modal fade" id="joinTournamentModalEl" tabindex="-1">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="joinTournamentModalTitleEl">Join Tournament</h5>
                    <button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button>
                </div>
                <div class="modal-body">
                    <form id="joinTournamentForm">
                        <input type="hidden" id="joinTournamentIdInput" />
                        <input type="hidden" id="joinTournamentFeeInput" />
                        <p class="text-center mb-3">Confirm entry for <strong id="joinFeeDisplayEl"></strong>?</p>
                        
                        <!-- Container for player inputs, will be populated by JS -->
                        <div id="joinPlayerInputsContainer" class="mb-3"></div>

                        <div class="mb-3">
                            <label class="form-label">Select Your Spot</label>
                            <div class="seat-selection-container" id="seatSelectionContainerEl">
                                <!-- Asientos generados por JS -->
                            </div>
                        </div>
                        <input type="hidden" id="selectedSeatInput" required>

                        <div id="joinTournamentStatusMessageEl" class="alert" style="display: none;"></div>
                        <div class="d-grid">
                            <button type="submit" class="btn btn-custom btn-custom-accent" id="confirmJoinBtnEl">Confirm & Pay</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Withdrawal Success Confirmation Modal -->
    <div class="modal fade" id="withdrawalSuccessModal" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-body">
                    <div class="success-icon">
                        <i class="fa-solid fa-check-circle"></i>
                    </div>
                    <h4>Withdrawal Request Submitted!</h4>
                    <p>
                        Your withdrawal request has been submitted successfully.
                        The amount will be credited to your account within <strong>30 minutes to 24 hours.</strong>
                        <br>
                        <small class="text-secondary">Note: Bank or network delays may occur.</small>
                    </p>
                    <button type="button" class="btn btn-confirm-ok" id="withdrawalSuccessOkBtn">OK, Got it</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Join Tournament Success Modal -->
    <div class="modal fade" id="joinSuccessModal" tabindex="-1" aria-hidden="true">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="modal-body">
                    <div class="success-icon" style="background: linear-gradient(135deg, #d1e7ff, #b6d4fa);">
                        <i class="fa-solid fa-gamepad" style="color: #0d6efd;"></i>
                    </div>
                    <h4>🎉 बधाई हो!</h4>
                    <p>
                        आपका Tournament Join सफल हो चुका है।
                        <br><br>
                        मैच शुरू होने के 10 मिनट पहले  
                        Room ID और Password आपके Notifications में भेज दिया जाएगा।
                    </p>
                    <button type="button" class="btn btn-confirm-ok" style="background: linear-gradient(45deg, #0d6efd, #0a58ca);" id="joinSuccessOkBtn">ठीक है</button>
                </div>
            </div>
        </div>
    </div>


    <!-- Bottom Navigation -->
    <nav class="bottom-nav">
        <button class="nav-item active" data-section="home-section"><i class="fa-solid fa-house-chimney"></i><span>Home</span></button>
        <button class="nav-item" data-section="matches-section"><i class="fa-solid fa-gamepad"></i><span>Matches</span></button>
        <button class="nav-item" data-section="wallet-section"><i class="fa-solid fa-wallet"></i><span>Wallet</span></button>
        <button class="nav-item" data-section="earnings-section"><i class="fa-solid fa-money-bill-wave"></i><span>Earnings</span></button>
        <button class="nav-item" data-section="profile-section"><i class="fa-solid fa-user-astronaut"></i><span>Profile</span></button>
    </nav>
    
  
    <!-- JS Libraries -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

    <!-- Firebase SDK & App Logic -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
        import { getDatabase, ref, get, set, update, push, query, orderByChild, equalTo, onValue, runTransaction, off, limitToLast, serverTimestamp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-database.js";
        import { getAuth, onAuthStateChanged, createUserWithEmailAndPassword, signInWithEmailAndPassword, sendPasswordResetEmail, signOut, GoogleAuthProvider, signInWithPopup, EmailAuthProvider, reauthenticateWithCredential, updatePassword } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-auth.js";
        // Import Firestore functions
        import { getFirestore, collection, doc, addDoc, setDoc, getDoc, deleteDoc, query as firestoreQuery, orderBy, onSnapshot, serverTimestamp as firestoreServerTimestamp, writeBatch, getDocs } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

        // -----------Add firebase api key  // @codefree genius  ------
        const firebaseConfig = {
          apiKey: "AIzaSyA6E9mHJMKKOal8aBNpk3X4y9M9QNsZKeU",
          authDomain: "rk-club-tournament-10b06.firebaseapp.com",
          databaseURL: "https://rk-club-tournament-10b06-default-rtdb.firebaseio.com",
          projectId: "rk-club-tournament-10b06",
          storageBucket: "rk-club-tournament-10b06.firebasestorage.app",
          messagingSenderId: "560422941390",
          appId: "1:560422941390:web:5d477a958bc37facf0d69f",
          measurementId: "G-VL6FB1RWTC"
        };

        let app, db, auth, firestore;
        try {
            app = initializeApp(firebaseConfig);
            db = getDatabase(app);
            auth = getAuth(app);
            firestore = getFirestore(app);
            console.log("Firebase Initialized successfully!");
        } catch (error) {
            console.error("Firebase initialization failed:", error);
            document.body.innerHTML = `<div class="alert alert-danger m-5">${error.message}</div>`;
        }

        const getElement = (id) => document.getElementById(id);
        const elements = {
            profileViewContainer: getElement('profile-view-container'),
            editProfileContainer: getElement('edit-profile-container'),
            helpCenterContainer: getElement('help-center-container'),
            loginForm: getElement('loginForm'),
            loginIdentifierInput: getElement('loginIdentifierInputEl'),
            loginPasswordInput: getElement('loginPasswordInputEl'),
            loginBtn: getElement('loginBtnEl'),
            loginStatusMessage: getElement('loginStatusMessageEl'),
            forgotPasswordLink: getElement('forgotPasswordLinkEl'),
            showSignupToggleBtn: getElement('showSignupToggleBtnEl'),
            signupForm: getElement('signupForm'),
            signupNameInput: getElement('signupNameInputEl'),
            signupEmailInput: getElement('signupEmailInputEl'),
            signupPhoneInput: getElement('signupPhoneInputEl'),
            signupPasswordInput: getElement('signupPasswordInputEl'),
            signupConfirmPasswordInput: getElement('signupConfirmPasswordInputEl'),
            signupReferralCodeInput: getElement('signupReferralCodeInputEl'),
            signupBtn: getElement('signupBtnEl'),
            signupStatusMessage: getElement('signupStatusMessageEl'),
            showLoginToggleBtn: getElement('showLoginToggleBtnEl'),
            forgotPasswordForm: getElement('forgotPasswordForm'),
            forgotEmailInput: getElement('forgotEmailInputEl'),
            sendResetLinkBtn: getElement('sendResetLinkBtnEl'),
            forgotStatusMessage: getElement('forgotStatusMessageEl'),
            backToLoginBtn: getElement('backToLoginBtnEl'),
            googleSignInBtn: getElement('googleSignInBtn'),
            googleSignInBtnSignup: getElement('googleSignInBtnSignup'), // ADDED
            sections: document.querySelectorAll('.section'), 
            bottomNavItems: document.querySelectorAll('.bottom-nav .nav-item'), 
            globalLoader: getElement('globalLoaderEl'),
            headerBackBtn: getElement('headerBackBtnEl'), 
            headerTitleContainer: getElement('headerTitleContainerEl'), 
            headerGameTitle: getElement('headerGameTitleEl'), 
            headerWalletChip: getElement('headerWalletChipEl'), 
            headerChipBalance: getElement('headerChipBalanceEl'), 
            headerUserGreeting: getElement('headerUserGreetingEl'), 
            appLogo: getElement('appLogoEl'), 
            notificationBtn: getElement('notificationBtnEl'), 
            notificationBadge: document.querySelector('.notification-badge'),
            homeSection: getElement('home-section'), 
            promotionSlider: getElement('promotionSliderEl'), 
            gamesList: getElement('gamesListEl'), 
            myContestsList: getElement('myContestsListEl'), 
            noContestsMessage: getElement('noContestsMessageEl'),
            homeCategoryTabs: getElement('homeCategoryTabs'),
            matchesCategoryTabs: getElement('matchesCategoryTabs'),
            homePageAdContainer: getElement('homePageAdContainer'), // Ad container

            // New Matches Section Elements
            matchesSection: getElement('matches-section'),
            allGamesListEl: getElement('allGamesListEl'),

            tournamentsSection: getElement('tournaments-section'), 
            tournamentsListContainer: getElement('tournamentsListContainerEl'), 
            noTournamentsMessage: getElement('noTournamentsMessageEl'), 
            tournamentTabs: document.querySelectorAll('#tournaments-section .tab-item'),
            
            walletSection: getElement('wallet-section'), 
            walletTotalBalance: getElement('walletTotalBalanceEl'), 
            walletWinningCash: getElement('walletWinningCashEl'), 
            walletBonusCash: getElement('walletBonusCashEl'), 
            allTransactionsBtn: getElement('allTransactionsBtnEl'), 
            withdrawBtn: getElement('withdrawBtnEl'), 
            addAmountWalletBtn: getElement('addAmountWalletBtnEl'), 
            recentTransactionsList: getElement('recentTransactionsListEl'), 
            noTransactionsMessage: getElement('noTransactionsMessageEl'),
            transactionsSection: getElement('transactions-section'),
            fullTransactionsListEl: getElement('fullTransactionsListEl'),
            noFullTransactionsMessageEl: getElement('noFullTransactionsMessageEl'),
            withdrawalHistoryListEl: getElement('withdrawalHistoryListEl'),
            noWithdrawalHistoryMessageEl: getElement('noWithdrawalHistoryMessageEl'),
            historyTabs: document.querySelectorAll('#historyTabs .nav-link'),
            earningsSection: getElement('earnings-section'),
            earningsHistorySection: getElement('earnings-history-section'),
            fullEarningsListEl: getElement('fullEarningsListEl'),
            noFullEarningsMessageEl: getElement('noFullEarningsMessageEl'),
            earningsTotal: getElement('earningsTotalEl'), 
            earningsReferral: getElement('earningsReferralEl'), 
            viewEarningsHistoryBtn: getElement('viewEarningsHistoryBtn'),
            topEarnersList: getElement('topEarnersListEl'),
            noTopEarnersMessage: getElement('noTopEarnersMessageEl'),
            profileSection: getElement('profile-section'), 
            profileAvatar: getElement('profileAvatarEl'), 
            profileName: getElement('profileNameEl'), 
            profileEmail: getElement('profileEmailEl'), 
            profileTotalMatches: getElement('profileTotalMatchesEl'), 
            profileWonMatches: getElement('profileWonMatchesEl'), 
            profileTotalEarnings: getElement('profileTotalEarningsEl'), 
            logoutProfileBtn: getElement('logoutProfileBtnEl'), 
            policyLinks: document.querySelectorAll('.profile-links a[data-policy]'), 
            notificationSwitch: getElement('notificationSwitchEl'),
            policyModalInstance: getElement('policyModalEl') ? new bootstrap.Modal(getElement('policyModalEl')) : null, 
            policyModalTitle: getElement('policyModalTitleEl'), 
            policyModalBody: getElement('policyModalBodyEl'),
            notificationModalInstance: getElement('notificationModalEl') ? new bootstrap.Modal(getElement('notificationModalEl')) : null, 
            notificationModalBody: getElement('notificationModalBodyEl'),
            addAmountModalInstance: getElement('addAmountModalEl') ? new bootstrap.Modal(getElement('addAmountModalEl')) : null,
            addAmountOptions: getElement('addAmountOptionsEl'),
            paymentInstructions: getElement('paymentInstructionsEl'),
            withdrawModalInstance: getElement('withdrawModalEl') ? new bootstrap.Modal(getElement('withdrawModalEl')) : null,
            withdrawalSuccessModalInstance: getElement('withdrawalSuccessModal') ? new bootstrap.Modal(getElement('withdrawalSuccessModal'), { backdrop: 'static', keyboard: false }) : null,
            withdrawalSuccessOkBtn: getElement('withdrawalSuccessOkBtn'),
            withdrawModalBalance: getElement('withdrawModalBalanceEl'),
            minWithdrawAmountUpi: getElement('minWithdrawAmountUpiEl'),
            minWithdrawAmountBank: getElement('minWithdrawAmountBankEl'),
            withdrawStatusMessage: getElement('withdrawStatusMessageEl'),
            withdrawUpiAmountInput: getElement('withdrawUpiAmountInputEl'), 
            withdrawUpiIdInput: getElement('withdrawUpiIdInputEl'), 
            submitUpiWithdrawBtn: getElement('submitUpiWithdrawBtnEl'),
            withdrawBankAmountInput: getElement('withdrawBankAmountInputEl'), 
            withdrawBankNameInput: getElement('withdrawBankNameInputEl'), 
            withdrawBankAccountInput: getElement('withdrawBankAccountInputEl'), 
            withdrawBankReAccountInput: getElement('withdrawBankReAccountInputEl'), 
            withdrawBankIfscInput: getElement('withdrawBankIfscInputEl'), 
            submitBankWithdrawBtn: getElement('submitBankWithdrawBtnEl'),
            matchDetailsModalInstance: getElement('matchDetailsModalEl') ? new bootstrap.Modal(getElement('matchDetailsModalEl')) : null, 
            matchDetailsModalTitle: getElement('matchDetailsModalTitleEl'), 
            matchDetailsModalBody: getElement('matchDetailsModalBodyEl'),
            idPasswordModalInstance: getElement('idPasswordModalEl') ? new bootstrap.Modal(getElement('idPasswordModalEl')) : null, 
            roomIdDisplay: getElement('roomIdDisplayEl'), 
            roomPasswordDisplay: getElement('roomPasswordDisplayEl'),
            securityWarning: getElement('securityWarning'),
            editProfileBtn: getElement('editProfileBtn'),
            cancelEditBtn: getElement('cancelEditBtn'),
            editProfileForm: getElement('editProfileForm'),
            avatarPreview: getElement('avatarPreview'),
            logoInput: getElement('logoInput'),
            nameInput: getElement('nameInput'),
            emailInput: getElement('emailInput'),
            editProfileStatusMessage: getElement('editProfileStatusMessageEl'),
            toastMessage: getElement('toast-message'),
            themeSwitch: getElement('themeSwitchEl'),
            helpCenterBtn: getElement('helpCenterBtn'),
            chatMessagesContainer: getElement('chatMessagesContainerEl'),
            chatMessageInput: getElement('chatMessageInputEl'),
            chatSendBtn: getElement('chatSendBtnEl'),
            joinTournamentModalInstance: getElement('joinTournamentModalEl') ? new bootstrap.Modal(getElement('joinTournamentModalEl')) : null,
            joinTournamentForm: getElement('joinTournamentForm'),
            joinTournamentIdInput: getElement('joinTournamentIdInput'),
            joinTournamentFeeInput: getElement('joinTournamentFeeInput'),
            joinFeeDisplayEl: getElement('joinFeeDisplayEl'),
            joinPlayerInputsContainer: getElement('joinPlayerInputsContainer'),
            seatSelectionContainer: getElement('seatSelectionContainerEl'),
            selectedSeatInput: getElement('selectedSeatInput'),
            joinTournamentStatusMessage: getElement('joinTournamentStatusMessageEl'),
            confirmJoinBtn: getElement('confirmJoinBtnEl'),
            joinSuccessModalInstance: getElement('joinSuccessModal') ? new bootstrap.Modal(getElement('joinSuccessModal'), { backdrop: 'static', keyboard: false }) : null,
            joinSuccessOkBtn: getElement('joinSuccessOkBtn'),
            changePasswordBtnEl: getElement('changePasswordBtnEl'),
            changePasswordModalInstance: getElement('changePasswordModalEl') ? new bootstrap.Modal(getElement('changePasswordModalEl')) : null,
            changePasswordForm: getElement('changePasswordForm'),
            oldPasswordInputEl: getElement('oldPasswordInputEl'),
            newPasswordInputEl: getElement('newPasswordInputEl'),
            confirmPasswordInputEl: getElement('confirmPasswordInputEl'),
            changePasswordStatusMessageEl: getElement('changePasswordStatusMessageEl'),
        };

        let currentUser = null; 
        let userProfile = {}; 
        let currentSectionId = 'login-section'; 
        let navigationHistory = []; // For back button functionality
        let dbListeners = {};
        let chatMessagesListenerUnsubscribe = null;
        let swiperInstance; 
        let adSwiperInstance; // For ads
        let currentTournamentGameId = null; 
        let appSettings = {};
        let allGamesCache = []; // NEW: Cache for all games
        let currentGameTournamentsCache = {};
        let isProfileSubViewVisible = false;
        let validatedReferrerInfo = null;

        // ===============================================
        // NEW: AUTO-ASSISTANT BOT FEATURE
        // ===============================================

        const botKnowledgeBase = {
            'account': "To manage your account, go to the 'Profile' section. You can edit your name, change your password, and view your stats.",
            'payment': "You can add money to your wallet using UPI. Go to the 'Wallet' section and click 'Add Amount'. For withdrawals, you need to have winnings in your 'Winning Cash' balance.",
            'deposit': "To add money, go to the 'Wallet' section, click 'Add Amount', select an option, and follow the payment instructions. Please send the screenshot to our WhatsApp after payment.",
            'withdraw': "You can withdraw your winnings from the 'Wallet' section. The minimum withdrawal amount is ₹50. It can take up to 24 hours to process.",
            'join': "To join a tournament, go to the 'Matches' section, select a game, and then choose an 'upcoming' tournament. Click the 'Join' button and fill in your details.",
            'rules': "You can find the rules for each tournament by clicking the 'Details' button on the tournament card.",
            'result': "Tournament results are available in the 'Results' tab of the respective game's tournament section after the match is completed.",
            'prize': "Prizes are distributed based on the prize pool and per-kill rewards mentioned in the tournament details. Winnings are added to your 'Winning Cash' in the wallet.",
            'id': "Room ID and Password will be available 10-15 minutes before the match starts. You can find it by clicking the 'View ID & Pass' button on the joined match card on the home screen, or in your notifications.",
            'password': "Room ID and Password will be available 10-15 minutes before the match starts. You can find it by clicking the 'View ID & Pass' button on the joined match card on the home screen, or in your notifications.",
            'app': "This app allows you to join gaming tournaments and win prizes. You can navigate using the bottom bar: Home, Matches, Wallet, Earnings, and Profile.",
            'hello': "Hello! I am your assistant. How can I help you today?",
            'hi': "Hello! I am your assistant. How can I help you today?",
            'help': "I can help with questions about your account, payments, joining tournaments, rules, and more. What do you need help with?",
            'default': "I'm sorry, I couldn't understand that. I am forwarding your query to our support team. An admin will get back to you shortly."
        };

        function getAutoReply(userMessage) {
            const message = userMessage.toLowerCase();
            for (const keyword in botKnowledgeBase) {
                if (message.includes(keyword)) {
                    return { response: botKnowledgeBase[keyword], escalated: keyword === 'default' };
                }
            }
            // This part is redundant because of the 'default' case, but it's a good fallback.
            return { response: botKnowledgeBase['default'], escalated: true };
        }

        async function checkAdminOnlineStatus() {
            // In a real application, this function would check a value in Firebase 
            // (e.g., using presence management) to see if an admin is active.
            // For this user-panel-only demonstration, we will always return false
            // to ensure the bot feature activates and responds.
            return false;
        }

        async function triggerAutoAssistant(userMessage) {
            if (!currentUser || !firestore) return;

            const isAdminOnline = await checkAdminOnlineStatus();
            if (isAdminOnline) {
                console.log("Admin is online. Bot will not reply.");
                return;
            }

            // Wait a few seconds to simulate the bot "thinking" and to give a real admin
            // a chance to see the message and reply first if they just came online.
            setTimeout(async () => {
                const botReply = getAutoReply(userMessage);
                const messagesRef = collection(firestore, 'HelpCenter', currentUser.uid, 'messages');
                
                try {
                    // Send the bot's message to the chat
                    await addDoc(messagesRef, {
                        sender: 'bot',
                        message: botReply.response,
                        timestamp: firestoreServerTimestamp()
                    });

                    // If the bot couldn't answer, mark the chat for admin review
                    if (botReply.escalated) {
                        await updateChatMetadata({ status: 'pending_admin' });
                    }
                } catch (error) {
                    console.error("Error sending bot message:", error);
                }

            }, 2500); // 2.5-second delay
        }

        // ===============================================
        // END OF AUTO-ASSISTANT BOT FEATURE
        // ===============================================

        
        const showLoader = (show) => { if (elements.globalLoader) elements.globalLoader.style.display = show ? 'flex' : 'none'; };
        function showStatusMessage(element, message, type = 'danger', autohide = true) { if (!element) return; element.innerHTML = message; element.className = `alert alert-${type} mt-3`; element.style.display = 'block'; element.setAttribute('role', 'alert'); if (autohide) { setTimeout(() => { if (element && element.innerHTML === message) element.style.display = 'none'; }, 8000); } } // Increased autohide time
        function clearStatusMessage(element) { if (!element) return; element.style.display = 'none'; element.innerHTML = ''; element.removeAttribute('role'); }
        function showToast(message) {
            if (elements.toastMessage) {
                elements.toastMessage.textContent = message;
                elements.toastMessage.classList.add('show');
                setTimeout(() => {
                    elements.toastMessage.classList.remove('show');
                }, 3000);
            }
        }
        function generateReferralCode(length = 8) { const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'; let result = ''; for (let i = 0; i < length; i++) result += chars.charAt(Math.floor(Math.random() * chars.length)); return result; }
        function getTimeRemaining(startTime) { if (!startTime) return 'TBA'; const now = Date.now(); const diff = startTime - now; if (diff <= 0) return 'Starting Soon'; const days = Math.floor(diff / 86400000); const hours = Math.floor((diff % 86400000) / 3600000); const minutes = Math.floor((diff % 3600000) / 60000); let o = ''; if (days > 0) o += `${days}d `; if (hours > 0 || days > 0) o += `${hours}h `; o += `${minutes}m`; return o.trim() || 'Now'; }
        const removePlaceholders = (parentElement) => { if (!parentElement) return; parentElement.classList.remove('placeholder-glow'); parentElement.querySelectorAll('.placeholder').forEach(el => el.remove()); };

        async function updateChatMetadata(data) {
            if (!currentUser || !firestore) return;
            const metadataRef = doc(firestore, 'HelpCenter', currentUser.uid);
            try {
                await setDoc(metadataRef, data, { merge: true });
            } catch (error) {
                console.error("Error updating chat metadata:", error);
            }
        }

        async function deleteChatHistory() {
            if (!currentUser || !firestore) return;
            console.log("Deleting chat history...");
            const metadataRef = doc(firestore, 'HelpCenter', currentUser.uid);
            const messagesRef = collection(firestore, 'HelpCenter', currentUser.uid, 'messages');

            try {
                const batch = writeBatch(firestore);
                const querySnapshot = await getDocs(messagesRef);
                querySnapshot.forEach((doc) => {
                    batch.delete(doc.ref);
                });
                batch.delete(metadataRef);
                await batch.commit();
                console.log("Chat history deleted successfully.");
            } catch (error) {
                console.error("Error deleting chat history:", error);
            }
        }


        function toggleProfileSubView(view) {
            isProfileSubViewVisible = (view !== 'main');
            elements.profileViewContainer.style.display = 'none';
            elements.editProfileContainer.style.display = 'none';
            elements.helpCenterContainer.style.display = 'none';
            if (view !== 'chat' && chatMessagesListenerUnsubscribe) {
                chatMessagesListenerUnsubscribe();
                chatMessagesListenerUnsubscribe = null;
                updateChatMetadata({ userClosedChat: true });
            }

            let targetSectionId = `profile-section-${view}`;
            
            if (view === 'main') {
                elements.profileViewContainer.style.display = 'block';
                targetSectionId = 'profile-section';
            } else if (view === 'edit') {
                elements.editProfileContainer.style.display = 'block';
            } else if (view === 'chat') {
                elements.helpCenterContainer.style.display = 'flex';
                loadHelpChat();
            }
            updateHeaderForSection(currentSectionId);

            // Manage history for sub-views
            if (navigationHistory[navigationHistory.length - 1] !== targetSectionId) {
                 showSection(targetSectionId);
            }
        }
        
        async function loadHelpChat() {
            if (!currentUser || !firestore) return;
            if (chatMessagesListenerUnsubscribe) return;

            const chatContainer = elements.chatMessagesContainer;
            chatContainer.innerHTML = '<p class="text-secondary text-center p-4">Loading recent messages...</p>';

            const metadataRef = doc(firestore, 'HelpCenter', currentUser.uid);
            const metadataSnap = await getDoc(metadataRef);
            const metadata = metadataSnap.exists() ? metadataSnap.data() : {};

            if (metadata.userClosedChat && metadata.adminSeen) {
                await deleteChatHistory();
            }

            await updateChatMetadata({ userClosedChat: false, adminSeen: false });

            const messagesRef = collection(firestore, 'HelpCenter', currentUser.uid, 'messages');
            const q = firestoreQuery(messagesRef, orderBy('timestamp', 'asc'));

            chatMessagesListenerUnsubscribe = onSnapshot(q, (querySnapshot) => {
                chatContainer.innerHTML = ''; 
                
                const allMessages = [];
                querySnapshot.forEach(doc => {
                    allMessages.push(doc.data());
                });

                // NEW LOGIC: Filter messages older than 24 hours
                const twentyFourHoursAgo = Date.now() - (24 * 60 * 60 * 1000);
                const recentMessages = allMessages.filter(msg => {
                    if (msg.timestamp && typeof msg.timestamp.toMillis === 'function') {
                        return msg.timestamp.toMillis() > twentyFourHoursAgo;
                    }
                    return false; 
                });

                if (recentMessages.length === 0) {
                    chatContainer.innerHTML = '<p class="text-secondary text-center p-4">Send a message to start the conversation. Messages older than 24 hours are hidden.</p>';
                    return;
                }

                recentMessages.forEach((message) => {
                    const messageType = (message.sender === 'user') ? 'sent' : 'received';

                    if (messageType === 'received') {
                        const senderLabel = document.createElement('div');
                        senderLabel.className = 'chat-sender-label';
                        senderLabel.style.alignSelf = 'flex-start';
                        
                        const senderIcon = message.sender === 'bot' ? 'fa-robot' : 'fa-user-shield';
                        const senderName = message.sender === 'bot' ? 'Robot Assistant' : 'Admin';
                        
                        senderLabel.innerHTML = `<i class="fa-solid ${senderIcon}"></i> ${senderName}`;
                        chatContainer.appendChild(senderLabel);
                    }
                    
                    const messageEl = document.createElement('div');
                    messageEl.className = `chat-message ${messageType}`;
                    messageEl.textContent = message.message;
                    chatContainer.appendChild(messageEl);
                });

                chatContainer.scrollTop = chatContainer.scrollHeight;
            }, (error) => {
                console.error("Error listening to chat messages:", error);
                chatContainer.innerHTML = '<p class="text-danger text-center p-4">Could not load chat. Please try again later.</p>';
            });
        }
        

        async function handleSendMessage() {
            if (!currentUser || !firestore) return;
            const messageInput = elements.chatMessageInput;
            const messageText = messageInput.value.trim();
            if (messageText === '') return;

            const messagesRef = collection(firestore, 'HelpCenter', currentUser.uid, 'messages');
            messageInput.disabled = true;
            try {
                // First, ensure the chat is marked as active by the user
                await updateChatMetadata({ userClosedChat: false });
                
                // Send the user's message
                await addDoc(messagesRef, {
                    sender: 'user',
                    message: messageText,
                    timestamp: firestoreServerTimestamp()
                });
                
                // Clear the input and trigger the auto-assistant logic
                const userMessageForBot = messageText;
                messageInput.value = '';
                triggerAutoAssistant(userMessageForBot); 

            } catch (error) {
                console.error("Error sending message:", error);
                showToast("Failed to send message.");
            } finally {
                messageInput.disabled = false;
                messageInput.focus();
            }
        }
        
        function handleHeaderBackClick() {
            window.history.back();
        }

        function handlePopState(event) {
            const poppedSection = navigationHistory.pop();
            const targetSection = navigationHistory[navigationHistory.length - 1];

            if (targetSection) {
                showSection(targetSection, true); 
            } else {
                // If history is empty, the user wants to exit.
                // We push the last section back so the URL doesn't look broken if they don't exit.
                if (poppedSection) {
                    navigationHistory.push(poppedSection);
                    // On most mobile browsers, calling history.back() when there's no more history
                    // will exit the PWA. We don't need to do anything further.
                }
            }
        }

        function showSection(sectionId, fromPopState = false) {
             const baseSectionId = sectionId.split('-')[0] + '-section';
             if (!auth || !baseSectionId || !elements.sections) { console.error("Cannot show section", sectionId); return; }
             const targetSection = getElement(baseSectionId); if (!targetSection) { console.error(`Section element "${baseSectionId}" not found.`); showSection(currentUser ? 'home-section' : 'login-section'); return; }
             const protectedSections = ['home-section', 'matches-section', 'wallet-section', 'earnings-section', 'profile-section', 'tournaments-section', 'transactions-section', 'earnings-history-section'];
             const isLoggedIn = !!currentUser;
             if (protectedSections.includes(baseSectionId) && !isLoggedIn) { showSection('login-section'); return; }
             if (baseSectionId === 'login-section' && isLoggedIn) { showSection('home-section'); return; }
             
             if (!fromPopState) {
                history.pushState({ section: sectionId }, '', `#${sectionId}`);
                if (navigationHistory[navigationHistory.length -1] !== sectionId) {
                    navigationHistory.push(sectionId);
                }
             }
             
             elements.sections.forEach(sec => sec.classList.remove('active')); 
             targetSection.classList.add('active'); 
             currentSectionId = sectionId;
             
             // Handle profile sub-views
             if (baseSectionId === 'profile-section') {
                isProfileSubViewVisible = sectionId !== 'profile-section';
                elements.profileViewContainer.style.display = sectionId === 'profile-section' ? 'block' : 'none';
                elements.editProfileContainer.style.display = sectionId === 'profile-section-edit' ? 'block' : 'none';
                elements.helpCenterContainer.style.display = sectionId === 'profile-section-chat' ? 'flex' : 'none';
                if (sectionId === 'profile-section-chat') loadHelpChat();
             } else {
                 isProfileSubViewVisible = false;
             }
            
             updateHeaderForSection(sectionId);

             elements.bottomNavItems.forEach(item => {
                const itemBaseSection = item.dataset.section;
                item.classList.toggle('active', itemBaseSection === baseSectionId);
             });
             
             // Data loading switch
             switch (baseSectionId) { // FIX: Use baseSectionId for loading
                 case 'home-section': loadHomePageData(); break;
                 case 'matches-section': loadAllGamesData(); break; 
                 case 'wallet-section': loadWalletData(); break;
                 case 'profile-section': loadProfileData(); break;
                 case 'earnings-section': loadEarningsData(); break;
                 case 'transactions-section':
                    new bootstrap.Tab(elements.historyTabs[0]).show();
                    loadFullTransactionHistory();
                    loadWithdrawalHistory();
                    break;
                 case 'earnings-history-section': loadFullEarningsHistory(); break;
                 case 'tournaments-section':
                    if(!currentTournamentGameId) {
                        elements.tournamentsListContainer.innerHTML = '<p class="text-secondary text-center mt-4">Select a game first.</p>';
                    }
                    break;
             }
             if (sectionId === 'login-section') { toggleAuthForm('login'); }
             window.scrollTo(0, 0);
         }

         function updateHeaderForSection(sectionId) {
            const isSubView = (
                sectionId === 'tournaments-section' ||
                sectionId === 'transactions-section' ||
                sectionId === 'earnings-history-section' ||
                isProfileSubViewVisible
            );

            elements.headerBackBtn.style.display = isSubView ? 'inline-block' : 'none';
            elements.headerTitleContainer.style.display = !isSubView ? 'block' : 'none';
            elements.headerGameTitle.style.display = isSubView ? 'block' : 'none';

            if (isSubView) {
                if (sectionId === 'tournaments-section' && currentTournamentGameId) {
                    elements.headerGameTitle.textContent = appSettings?.games?.[currentTournamentGameId]?.name || `Game`;
                } else if (sectionId === 'transactions-section') {
                    elements.headerGameTitle.textContent = "History";
                } else if (sectionId === 'earnings-history-section') {
                    elements.headerGameTitle.textContent = "Earnings History";
                } else if (sectionId.startsWith('profile-section-')) {
                     if (sectionId === 'profile-section-chat') {
                        elements.headerGameTitle.textContent = "Help Center";
                    } else if (sectionId === 'profile-section-edit') {
                        elements.headerGameTitle.textContent = "Edit Profile";
                    }
                }
            } else if (elements.headerUserGreeting) {
                const nameToShow = userProfile?.displayName || 'Guest';
                elements.headerUserGreeting.textContent = nameToShow;
            }
        }

        function initializeEventListeners() {
            window.addEventListener('popstate', handlePopState);
            elements.loginBtn.addEventListener('click', handleLogin);
            elements.signupBtn.addEventListener('click', handleSignup);
            elements.forgotPasswordLink.addEventListener('click', (e) => { e.preventDefault(); toggleAuthForm('forgot'); });
            elements.sendResetLinkBtn.addEventListener('click', handleForgotPassword);
            elements.googleSignInBtn.addEventListener('click', handleGoogleSignIn);
            elements.googleSignInBtnSignup.addEventListener('click', handleGoogleSignIn); // ADDED
            elements.showSignupToggleBtn.addEventListener('click', () => toggleAuthForm('signup'));
            elements.showLoginToggleBtn.addEventListener('click', () => toggleAuthForm('login'));
            elements.backToLoginBtn.addEventListener('click', () => toggleAuthForm('login'));
            elements.bottomNavItems?.forEach(item => item.addEventListener('click', (e) => { e.preventDefault(); showSection(item.dataset.section); }));
            
            elements.headerBackBtn?.addEventListener('click', handleHeaderBackClick);
            
            elements.tournamentTabs?.forEach(tab => tab.addEventListener('click', (e) => {
                const status = e.currentTarget.dataset.status;
                if (currentTournamentGameId && status) {
                    elements.tournamentTabs.forEach(t => t.classList.remove('active'));
                    e.currentTarget.classList.add('active');
                    renderFilteredTournaments();
                }
            }));

            elements.historyTabs?.forEach(tab => {
                tab.addEventListener('shown.bs.tab', (event) => {
                    if(event.target.id === 'all-transactions-tab'){
                        loadFullTransactionHistory();
                    } else if (event.target.id === 'withdrawals-tab'){
                        loadWithdrawalHistory();
                    }
                });
            });

            elements.logoutProfileBtn?.addEventListener('click', logoutUser);
            elements.policyLinks?.forEach(link => link.addEventListener('click', handlePolicyClick));
            elements.withdrawBtn?.addEventListener('click', handleWithdrawClick);
            elements.addAmountWalletBtn?.addEventListener('click', handleAddAmountClick);
            elements.addAmountOptions.querySelectorAll('button').forEach(btn => {
               btn.addEventListener('click', () => { elements.paymentInstructions.style.display = 'block'; });
            });
            elements.submitUpiWithdrawBtn?.addEventListener('click', (e) => {
               const btn = e.currentTarget;
               const amt = parseFloat(elements.withdrawUpiAmountInput.value);
               const upiId = elements.withdrawUpiIdInput.value.trim();
               if (!upiId) { showStatusMessage(elements.withdrawStatusMessage, 'Enter UPI ID.', 'warning'); return; }
               const details = { methodName: 'UPI', accountInfo: upiId };
               submitWithdrawRequestHandler(btn, amt, details);
            });
            elements.submitBankWithdrawBtn?.addEventListener('click', (e) => {
               const btn = e.currentTarget;
               const amt = parseFloat(elements.withdrawBankAmountInput.value);
               const name = elements.withdrawBankNameInput.value.trim();
               const accNum = elements.withdrawBankAccountInput.value.trim();
               const reAccNum = elements.withdrawBankReAccountInput.value.trim();
               const ifsc = elements.withdrawBankIfscInput.value.trim();
               if (!name || !accNum || !reAccNum || !ifsc) { showStatusMessage(elements.withdrawStatusMessage, 'Fill all bank details.', 'warning'); return; }
               if (accNum !== reAccNum) { showStatusMessage(elements.withdrawStatusMessage, 'Account numbers do not match.', 'warning'); return; }
               const details = { methodName: 'Bank', accountInfo: `Name: ${name}, A/C: ${accNum}, IFSC: ${ifsc}` };
               submitWithdrawRequestHandler(btn, amt, details);
            });
            
            elements.notificationBtn?.addEventListener('click', handleNotificationClick);

            elements.allTransactionsBtn?.addEventListener('click', () => showSection('transactions-section'));
            elements.viewEarningsHistoryBtn?.addEventListener('click', () => showSection('earnings-history-section'));
            
            // ==========================================================
            // FIX: Add preventDefault() to prevent page jump/reload
            // ==========================================================
            elements.helpCenterBtn?.addEventListener('click', (e) => {
                e.preventDefault();
                showSection('profile-section-chat');
            });
            
            elements.editProfileBtn.addEventListener('click', (e) => {
                e.preventDefault();
                showSection('profile-section-edit');
            });
            // ==========================================================
            
            elements.cancelEditBtn.addEventListener('click', () => showSection('profile-section'));
            
            elements.editProfileForm.addEventListener('submit', handleProfileUpdate);
            elements.logoInput.addEventListener('change', () => {
                const file = elements.logoInput.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = (e) => { elements.avatarPreview.src = e.target.result; };
                    reader.readAsDataURL(file);
                }
            });

            elements.themeSwitch?.addEventListener('change', () => {
                document.body.classList.toggle('light-mode', !elements.themeSwitch.checked);
                localStorage.setItem('theme', elements.themeSwitch.checked ? 'dark' : 'light');
            });

            elements.notificationSwitch?.addEventListener('change', () => {
                const isEnabled = elements.notificationSwitch.checked;
                localStorage.setItem('notificationsEnabled', isEnabled);
                updateNotificationIconVisibility();
                 if (!isEnabled && elements.notificationBadge) {
                    elements.notificationBadge.style.display = 'none';
                }
            });

            // =========================================================================
            //  MODIFIED COPY FUNCTION: Works on HTTP and Webview with Fallback
            // =========================================================================
            document.body.addEventListener('click', (event) => {
               const copyBtn = event.target.closest('.copy-btn');
               if (copyBtn) {
                   // Stop default action
                   event.preventDefault(); 

                   let textToCopy = copyBtn.dataset.copyText;
                   if (!textToCopy && copyBtn.dataset.target) {
                       const targetEl = document.querySelector(copyBtn.dataset.target);
                       if(targetEl) textToCopy = targetEl.textContent;
                   }
                   
                   if (textToCopy) {
                       const finalStats = textToCopy.trim();
                       // Try Modern Async API first (Works on HTTPS)
                       if (navigator.clipboard && window.isSecureContext) {
                           navigator.clipboard.writeText(finalStats)
                               .then(() => showToast('Copied!'))
                               .catch(err => {
                                   // If failed (e.g. permission denied or http), try fallback
                                   doFallbackCopy(finalStats);
                               });
                       } else {
                           // Fallback for HTTP or older browsers/webviews
                           doFallbackCopy(finalStats);
                       }
                   }
               }
            });

            // Helper function for fallback copy (Old School Method)
            function doFallbackCopy(text) {
                const textArea = document.createElement("textarea");
                textArea.value = text;
                textArea.style.position = "fixed"; // prevent scrolling to bottom
                textArea.style.left = "-9999px";
                textArea.style.top = "0";
                document.body.appendChild(textArea);
                textArea.focus();
                textArea.select();
                try {
                    const successful = document.execCommand('copy');
                    if(successful) showToast('Copied!');
                    else showToast('Copy failed manually');
                } catch (err) {
                    console.error('Fallback copy failed', err);
                    showToast('Copy failed');
                }
                document.body.removeChild(textArea);
            }
            // =========================================================================

            // ADDED: Event listener for show/hide password
            document.body.addEventListener('click', function(event) {
                if (event.target.classList.contains('toggle-password')) {
                    const passwordInput = event.target.previousElementSibling;
                    if (passwordInput && (passwordInput.type === 'password' || passwordInput.type === 'text')) {
                        // Toggle the type
                        const type = passwordInput.getAttribute('type') === 'password' ? 'text' : 'password';
                        passwordInput.setAttribute('type', type);
                        // Toggle the icon
                        event.target.classList.toggle('bi-eye-slash');
                        event.target.classList.toggle('bi-eye');
                    }
                }
            });

            elements.chatSendBtn.addEventListener('click', handleSendMessage);
            elements.chatMessageInput.addEventListener('keypress', (event) => {
                if (event.key === 'Enter' && !event.shiftKey) {
                    event.preventDefault();
                    handleSendMessage();
                }
            });
            
            elements.joinTournamentForm.addEventListener('submit', handleConfirmJoin);
            
            elements.withdrawalSuccessOkBtn.addEventListener('click', () => {
                elements.withdrawalSuccessModalInstance.hide();
                showSection('transactions-section');
                const withdrawalsTab = getElement('withdrawals-tab');
                if(withdrawalsTab) {
                    new bootstrap.Tab(withdrawalsTab).show();
                }
            });

            elements.joinSuccessOkBtn.addEventListener('click', () => {
                elements.joinSuccessModalInstance.hide();
            });

            elements.changePasswordBtnEl?.addEventListener('click', openChangePasswordModal);
            elements.changePasswordForm?.addEventListener('submit', handleChangePassword);
        }
        
        document.addEventListener('DOMContentLoaded', () => {
             const splashScreen = document.getElementById('splash-screen');
             if (splashScreen) {
                 setTimeout(() => {
                     splashScreen.classList.add('hide');
                     setTimeout(() => {
                         splashScreen.style.display = 'none';
                     }, 4000);
                 }, 4000);
             }

             applyTheme();
             applyNotificationSetting();

             if (!db || !firestore) { return; }
             showLoader(true);
             loadAppSettings()
                 .then(() => {
                     initializeEventListeners();
                     setupRealtimeAdsListener(); // Set up the real-time ad listener
                     onAuthStateChanged(auth, handleAuthStateChange);
                 })
                 .catch(err => {
                     console.error("CRITICAL: Initial settings load failed:", err);
                     alert("Error loading essential app settings. Please try again later.");
                     initializeEventListeners();
                     onAuthStateChanged(auth, handleAuthStateChange);
                 }).finally(() => {
                    showLoader(false);
                 });
        });
        
        // MODIFIED handleAuthStateChange to include the creation of referralCodeToUid entry
        async function handleAuthStateChange(user) {
            if (!auth || !db) return;
            showLoader(true);
            detachAllDbListeners();
            currentUser = user;
            
            const splashUsernameEl = document.getElementById('splash-username');

            if (user) {
                const userRef = ref(db, `users/${user.uid}`);
                try {
                    const snapshot = await get(userRef);
                    if (snapshot.exists()) {
                        userProfile = snapshot.val();
                    } else {
                        const name = elements.signupNameInput.value.trim() || user.displayName;
                        const phone = elements.signupPhoneInput.value.trim();
                        
                        let newUserBonus = 0;
                        if (validatedReferrerInfo && appSettings.referralBonus && appSettings.referralBonus > 0) {
                            newUserBonus = parseFloat(appSettings.referralBonus);
                        }
                        
                        const newReferralCode = generateReferralCode();
                        const newUserProfile = {
                            uid: user.uid,
                            displayName: name || 'New User',
                            email: user.email,
                            phone: phone,
                            photoURL: user.photoURL || '',
                            createdAt: serverTimestamp(),
                            balance: 0,
                            winningCash: 0,
                            bonusCash: newUserBonus,
                            totalMatches: 0,
                            wonMatches: 0,
                            totalEarnings: 0,
                            referralEarnings: 0,
                            joinedTournaments: {},
                            isAdmin: false,
                            referralCode: newReferralCode,
                            referredBy: validatedReferrerInfo ? validatedReferrerInfo.uid : null
                        };
                        await set(userRef, newUserProfile);
                        
                        // Create the referralCodeToUid mapping
                        const referralCodeRef = ref(db, `referralCodeToUid/${newReferralCode}`);
                        await set(referralCodeRef, { uid: user.uid });

                        if(phone){
                            const phoneRef = ref(db, `phoneToUid/${phone}`);
                            await set(phoneRef, { uid: user.uid });
                        }

                        userProfile = newUserProfile;

                        if (newUserBonus > 0 && validatedReferrerInfo) {
                            await recordTransaction(
                                user.uid, 'referral_bonus', newUserBonus,
                                `Bonus for using referral from ${validatedReferrerInfo.displayName}`, 
                                { referrerId: validatedReferrerInfo.uid }
                            );
                        }

                        if (validatedReferrerInfo) {
                            const referrerBonus = parseFloat(appSettings.referrerBonus || appSettings.referralBonus || 0);
                            
                            if (referrerBonus > 0) {
                                const referrerRef = ref(db, `users/${validatedReferrerInfo.uid}`);
                                try {
                                    await runTransaction(referrerRef, (profile) => {
                                        if (profile) {
                                            profile.bonusCash = (profile.bonusCash || 0) + referrerBonus;
                                            profile.referralEarnings = (profile.referralEarnings || 0) + referrerBonus;
                                        }
                                        return profile;
                                    });

                                    await recordTransaction(
                                        validatedReferrerInfo.uid, 'referral_earning', referrerBonus,
                                        `Bonus for inviting ${newUserProfile.displayName}`, 
                                        { invitedUserId: user.uid }
                                    );

                                    const notificationsRef = ref(db, `notifications/${validatedReferrerInfo.uid}`);
                                    await push(notificationsRef, {
                                        title: 'Referral Bonus!',
                                        message: `🎉 You earned ₹${referrerBonus} bonus cash for inviting ${newUserProfile.displayName}!`,
                                        timestamp: serverTimestamp(),
                                        read: false
                                    });

                                    console.log(`Referrer ${validatedReferrerInfo.uid} has been rewarded with ₹${referrerBonus}.`);
                                } catch (e) {
                                    console.error("Failed to reward the referrer:", e);
                                }
                            }
                            
                            const referralsRef = ref(db, 'referrals');
                            await push(referralsRef, {
                                new_user_id: user.uid,
                                referrer_user_id: validatedReferrerInfo.uid,
                                bonus_amount_new_user: newUserBonus,
                                bonus_amount_referrer: referrerBonus,
                                date: serverTimestamp()
                            });
                            
                            validatedReferrerInfo = null;
                        }
                        
                        elements.signupForm.reset();
                        if (elements.signupReferralCodeInput) elements.signupReferralCodeInput.value = '';
                    }

                    if (splashUsernameEl) {
                        splashUsernameEl.textContent = userProfile.displayName || 'Player';
                    }
                    populateUserInfo(user, userProfile);
                    setupRealtimeListeners(user.uid);
                    updateGlobalUI(true);

                    navigationHistory = ['home-section'];
                    history.replaceState({ section: 'home-section' }, '', '#home-section');
                    showSection('home-section', true);

                } catch (error) {
                    console.error("Profile handling error:", error);
                    alert("Error loading profile. Logging out.");
                    await logoutUser();
                }
            } else {
                currentUser = null;
                userProfile = {};
                if (splashUsernameEl) {
                    splashUsernameEl.textContent = 'Player';
                }
                updateGlobalUI(false);
                
                navigationHistory = ['login-section'];
                history.replaceState({ section: 'login-section' }, '', '#login-section');
                showSection('login-section', true);
            }
            showLoader(false);
        }

        // Helper function to render HTML string with executable scripts
        function renderHtmlWithScripts(container, htmlString) {
            if (!container) return;
            container.innerHTML = htmlString;
            const scripts = Array.from(container.querySelectorAll("script"));
            for (const oldScript of scripts) {
                const newScript = document.createElement("script");
                for (const attr of oldScript.attributes) {
                    newScript.setAttribute(attr.name, attr.value);
                }
                newScript.appendChild(document.createTextNode(oldScript.innerHTML));
                oldScript.parentNode.replaceChild(newScript, oldScript);
            }
        }

        // FINAL & CORRECTED: Real-time listener for ads
        function setupRealtimeAdsListener() {
            if (!db) return;
            // This path is correct according to your admin panel setup
            const adNodeRef = ref(db, 'ads_code'); 
            
            onValue(adNodeRef, (snapshot) => {
                const adData = snapshot.val();
                // We need to read the 'htmlCode' key from the fetched data
                const adCode = adData ? adData.htmlCode : null; 
                
                const adContainerWrapper = elements.homePageAdContainer?.querySelector('.swiper-wrapper');

                if (!adContainerWrapper) {
                    console.error("Ad container wrapper not found.");
                    return;
                }

                adContainerWrapper.innerHTML = '';
                
                if (adCode && typeof adCode === 'string' && adCode.trim() !== '') {
                    const slide = document.createElement('div');
                    slide.className = 'swiper-slide';
                    slide.style.display = 'flex';
                    slide.style.justifyContent = 'center';
                    slide.style.alignItems = 'center';
                    slide.style.backgroundColor = 'var(--secondary-bg)';
                    
                    const adContentContainer = document.createElement('div');
                    adContentContainer.style.minHeight = '50px';
                    adContentContainer.style.display = 'flex';
                    adContentContainer.style.alignItems = 'center';
                    adContentContainer.style.justifyContent = 'center';
                    
                    renderHtmlWithScripts(adContentContainer, adCode);

                    slide.appendChild(adContentContainer);
                    adContainerWrapper.appendChild(slide);

                    if (adSwiperInstance) {
                        adSwiperInstance.destroy(true, true);
                    }
                    adSwiperInstance = new Swiper(elements.homePageAdContainer, {
                        loop: false,
                        autoplay: { delay: 5000, disableOnInteraction: false, },
                        slidesPerView: 1, observer: true, observeParents: true,
                    });
                    elements.homePageAdContainer.style.display = 'block';

                } else {
                    if (adSwiperInstance) {
                        adSwiperInstance.destroy(true, true);
                        adSwiperInstance = null;
                    }
                    elements.homePageAdContainer.style.display = 'none';
                }

            }, (error) => {
                console.error("Failed to set up real-time ad listener:", error);
            });
        }


        function showEditProfileForm() { if(!currentUser || !userProfile) return; elements.nameInput.value = userProfile.displayName || ''; elements.emailInput.value = currentUser.email || ''; elements.avatarPreview.src = userProfile.photoURL || `https://ui-avatars.com/api/?name=${encodeURIComponent(userProfile.displayName || 'U')}&background=0F172A&color=E2E8F0&bold=true&size=100`; elements.logoInput.value = ''; clearStatusMessage(elements.editProfileStatusMessage); toggleProfileSubView('edit'); }
        async function handleProfileUpdate(event) { event.preventDefault(); if(!currentUser) return; const newName = elements.nameInput.value.trim(); const newLogoFile = elements.logoInput.files[0]; if(!newName) { showStatusMessage(elements.editProfileStatusMessage, "Name cannot be empty.", "warning"); return; } showLoader(true); const userRef = ref(db, `users/${currentUser.uid}`); const updates = { displayName: newName }; try { if (newLogoFile) { const dataUrl = await new Promise((resolve, reject) => { const reader = new FileReader(); reader.onload = () => resolve(reader.result); reader.onerror = reject; reader.readAsDataURL(newLogoFile); }); updates.photoURL = dataUrl; } await update(userRef, updates); showToast("Profile updated successfully!"); showSection('profile-section'); } catch (error) { console.error("Profile update error:", error); showStatusMessage(elements.editProfileStatusMessage, "Failed to update profile. Please try again.", "danger"); } finally { showLoader(false); } }
        async function loadAppSettings() { try { const settingsRef = ref(db, 'settings'); const snapshot = await get(settingsRef); if (snapshot.exists()) { appSettings = snapshot.val() || {}; if (appSettings.logoUrl && elements.appLogo) elements.appLogo.src = appSettings.logoUrl; if (appSettings.minWithdraw) { if (elements.minWithdrawAmountUpi) elements.minWithdrawAmountUpi.textContent = appSettings.minWithdraw; if (elements.minWithdrawAmountBank) elements.minWithdrawAmountBank.textContent = appSettings.minWithdraw; } } else { console.warn("App Settings not found in database!"); appSettings = {}; } } catch (e) { console.error("Could not load App Settings from Firebase.", e); appSettings = {}; alert("Could not load app settings."); } }
        
        function loadHomePageData() { 
            if (!currentUser) { 
                if(elements.promotionSlider?.querySelector('.swiper-wrapper')) elements.promotionSlider.querySelector('.swiper-wrapper').innerHTML = ''; 
                if(elements.gamesList) elements.gamesList.innerHTML = ''; 
                if(elements.myContestsList) elements.myContestsList.innerHTML = '<p class="text-secondary text-center">Login to view contests.</p>'; 
                return; 
            } 
            loadPromotions();
            loadGames(true); // Pass true for home
            loadMyContests(); 
        }
        
        async function loadPromotions() { if (!elements.promotionSlider) return; const sliderWrapper = elements.promotionSlider.querySelector('.swiper-wrapper'); if (!sliderWrapper) return; sliderWrapper.classList.add('placeholder-glow'); sliderWrapper.innerHTML = `<div class="swiper-slide"><span class="placeholder" style="height: 100%; border-radius: 10px; display: block; width: 100%;"></span></div>`; const promoRef = ref(db, 'promotions'); try { const snapshot = await get(promoRef); const promotions = snapshot.val() || {}; const activePromotions = Object.values(promotions).filter(p => p.imageUrl); removePlaceholders(elements.promotionSlider); sliderWrapper.innerHTML = ''; if (activePromotions.length > 0) { elements.promotionSlider.style.display = 'block'; activePromotions.forEach(promo => { const slide = document.createElement('div'); slide.className = 'swiper-slide'; slide.innerHTML = promo.link ? `<a href="${promo.link}" target="_blank"><img src="${promo.imageUrl}" alt="Promo"></a>` : `<img src="${promo.imageUrl}" alt="Promo">`; sliderWrapper.appendChild(slide); }); if (swiperInstance) swiperInstance.destroy(true, true); swiperInstance = new Swiper(elements.promotionSlider, { loop: activePromotions.length > 1, autoplay: { delay: 3500, disableOnInteraction: false }, pagination: { el: '.swiper-pagination', clickable: true }, slidesPerView: 1 }); } else { elements.promotionSlider.style.display = 'none'; } } catch (e) { console.error("Promo load failed:", e); removePlaceholders(elements.promotionSlider); sliderWrapper.innerHTML = '<p class="text-danger text-center small p-3">Could not load promotions.</p>'; elements.promotionSlider.style.display = 'block'; } }
        
        async function loadGames(isHome = false) {
            const containerEl = isHome ? elements.gamesList : elements.allGamesListEl;
            if (!containerEl) return;
            
            containerEl.classList.add('placeholder-glow');
            containerEl.innerHTML = `<div class="col-12"><div class="game-card custom-card"><span class="placeholder d-block" style="height: 0; padding-bottom: 56.25%;"></span><span class="placeholder d-block mt-2 col-8 mx-auto" style="height: 20px;"></span></div></div> <div class="col-12"><div class="game-card custom-card"><span class="placeholder d-block" style="height: 0; padding-bottom: 56.25%;"></span><span class="placeholder d-block mt-2 col-8 mx-auto" style="height: 20px;"></span></div></div>`;
            
            try {
                const gamesRef = ref(db, 'games');
                const snapshot = await get(gamesRef);
                const games = snapshot.val() || {};
                allGamesCache = Object.entries(games)
                    .filter(([, game]) => game.imageUrl && game.name)
                    .sort(([, gameA], [, gameB]) => (gameA.order || 0) - (gameB.order || 0));

                if (!appSettings.games) appSettings.games = {};
                allGamesCache.forEach(([gameId, game]) => {
                    appSettings.games[gameId] = { name: game.name };
                });
                
                populateGameCategories(isHome);
                filterAndDisplayGames('All Games', isHome);

            } catch (e) {
                console.error("Games load failed:", e);
                removePlaceholders(containerEl);
                containerEl.innerHTML = '<p class="text-danger text-center col-12">Could not load games.</p>';
            }
        }
        
        function populateGameCategories(isHome) {
            const containerEl = isHome ? elements.homeCategoryTabs : elements.matchesCategoryTabs;
            if (!containerEl) return;

            // --- FIX START: Ensure Free Fire and BGMI are explicitly listed ---
            const categories = ['All Games', 'Free Fire', 'BGMI', 'Ludo', 'Clash Squad', 'Other'];
            // --- FIX END ---

            containerEl.innerHTML = ''; // Clear previous tabs

            categories.forEach(category => {
                const tab = document.createElement('button');
                tab.className = 'category-tab-item';
                tab.textContent = category;
                tab.dataset.category = category;
                if (category === 'All Games') {
                    tab.classList.add('active');
                }
                tab.addEventListener('click', () => {
                    filterAndDisplayGames(category, isHome);
                });
                containerEl.appendChild(tab);
            });
        }
        
        function filterAndDisplayGames(category, isHome) {
            const containerEl = isHome ? elements.gamesList : elements.allGamesListEl;
            const categoryContainerEl = isHome ? elements.homeCategoryTabs : elements.matchesCategoryTabs;
            if (!containerEl) return;

            // Update active tab
            categoryContainerEl.querySelectorAll('.category-tab-item').forEach(tab => {
                tab.classList.toggle('active', tab.dataset.category === category);
            });

            removePlaceholders(containerEl);
            containerEl.innerHTML = '';

            // --- FIX START: Case-Insensitive Filtering ---
            const filteredGames = category === 'All Games' 
                ? allGamesCache 
                : allGamesCache.filter(([, game]) => {
                    // Normalize both strings to lower case and trim spaces for safer comparison
                    // This fixes issues where Admin Panel saves "free fire" but App expects "Free Fire"
                    return game.category && game.category.toString().trim().toLowerCase() === category.trim().toLowerCase();
                });
            // --- FIX END ---

            if (filteredGames.length > 0) {
                filteredGames.forEach(([gameId, game]) => {
                    const col = document.createElement('div');
                    col.className = 'col-12';
                    col.innerHTML = `<div class="game-card custom-card" data-game-id="${gameId}" data-game-name="${game.name}"><img src="${game.imageUrl}" alt="${game.name}"><span>${game.name}</span></div>`;
                    col.querySelector('.game-card').addEventListener('click', () => {
                        currentTournamentGameId = gameId;
                        loadTournamentsForGame(gameId, game.name);
                    });
                    containerEl.appendChild(col);
                });
            } else {
                containerEl.innerHTML = `<p class="text-secondary text-center col-12">No games available in this category.</p>`;
            }
        }

        async function loadAllGamesData() {
            loadGames(false); // Pass false for matches page
        }
        
        function updateGlobalUI(isLoggedIn) { if (elements.headerWalletChip) { elements.headerWalletChip.style.display = isLoggedIn ? 'flex' : 'none'; if (isLoggedIn) elements.headerWalletChip.onclick = () => showSection('wallet-section'); else elements.headerWalletChip.onclick = null; } if (!isLoggedIn && elements.headerUserGreeting) elements.headerUserGreeting.textContent = 'Guest'; if (!isLoggedIn && elements.headerChipBalance) elements.headerChipBalance.textContent = '0'; elements.bottomNavItems.forEach(item => { const section = item.dataset.section; if (section === 'home-section' || section === 'matches-section' || isLoggedIn) { item.style.display = 'flex'; } else { item.style.display = 'none'; } }); if(isLoggedIn) loadUnreadNotificationCount(); else if(elements.notificationBadge) { elements.notificationBadge.style.display = 'none'; elements.notificationBadge.textContent = ''; } }
        function populateUserInfo(user, profile) { if (!user || !profile) return; const displayName = profile.displayName || user.displayName || user.email?.split('@')[0] || user.phoneNumber || 'User'; const photoURL = profile.photoURL || user.photoURL || `https://ui-avatars.com/api/?name=${encodeURIComponent(displayName)}&background=0F172A&color=E2E8F0&bold=true&size=70`; const balance = (profile.balance || 0); const winningCash = (profile.winningCash || 0); const bonusCash = (profile.bonusCash || 0); const totalEarnings = (profile.totalEarnings || 0); const referralEarnings = (profile.referralEarnings || 0); const totalMatches = profile.totalMatches || 0; const wonMatches = profile.wonMatches || 0; const formatCurrency = (amount) => `₹${amount.toFixed(2)}`; if (elements.appLogo) elements.appLogo.src = photoURL; if (elements.headerUserGreeting) elements.headerUserGreeting.textContent = displayName; if (elements.headerChipBalance) elements.headerChipBalance.textContent = Math.floor(balance); if (elements.walletTotalBalance) { elements.walletTotalBalance.textContent = formatCurrency(balance); removePlaceholders(elements.walletTotalBalance.closest('.placeholder-glow')); } if (elements.walletWinningCash) { elements.walletWinningCash.textContent = formatCurrency(winningCash); removePlaceholders(elements.walletWinningCash.closest('.placeholder-glow')); } if (elements.walletBonusCash) { elements.walletBonusCash.textContent = formatCurrency(bonusCash); removePlaceholders(elements.walletBonusCash.closest('.placeholder-glow')); } if (elements.withdrawModalBalance) elements.withdrawModalBalance.textContent = formatCurrency(winningCash); if (elements.profileAvatar) elements.profileAvatar.src = photoURL; if (elements.profileName) { elements.profileName.textContent = displayName; removePlaceholders(elements.profileName.closest('.placeholder-glow')); } if (elements.profileEmail) { elements.profileEmail.textContent = user.email || profile.email || 'N/A'; removePlaceholders(elements.profileEmail.closest('.placeholder-glow')); } if (elements.profileTotalMatches) { elements.profileTotalMatches.textContent = totalMatches; removePlaceholders(elements.profileTotalMatches.closest('.placeholder-glow')); } if (elements.profileWonMatches) { elements.profileWonMatches.textContent = wonMatches; removePlaceholders(elements.profileWonMatches.closest('.placeholder-glow')); } if (elements.profileTotalEarnings) { elements.profileTotalEarnings.textContent = formatCurrency(totalEarnings); removePlaceholders(elements.profileTotalEarnings.closest('.placeholder-glow')); } if (elements.earningsTotal) { elements.earningsTotal.textContent = formatCurrency(totalEarnings); removePlaceholders(elements.earningsTotal.closest('.placeholder-glow')); } if (elements.earningsReferral) { elements.earningsReferral.textContent = formatCurrency(referralEarnings); removePlaceholders(elements.earningsReferral.closest('.placeholder-glow')); } }
        function toggleAuthForm(formToShow) { clearStatusMessage(elements.loginStatusMessage); clearStatusMessage(elements.signupStatusMessage); clearStatusMessage(elements.forgotStatusMessage); elements.loginForm.style.display = (formToShow === 'login') ? 'block' : 'none'; elements.signupForm.style.display = (formToShow === 'signup') ? 'block' : 'none'; elements.forgotPasswordForm.style.display = (formToShow === 'forgot') ? 'block' : 'none'; }
        
        async function handleLogin() {
            const identifier = elements.loginIdentifierInput.value.trim();
            const password = elements.loginPasswordInput.value;
            if (!identifier || !password) {
                showStatusMessage(elements.loginStatusMessage, 'Please enter email/phone and password.', 'warning');
                return;
            }
            showLoader(true);
            clearStatusMessage(elements.loginStatusMessage);
            try {
                let userEmail = identifier;
                const isEmail = identifier.includes('@');

                if (!isEmail) {
                    const phoneToUidRef = ref(db, `phoneToUid/${identifier}`);
                    const phoneSnapshot = await get(phoneToUidRef);

                    if (phoneSnapshot.exists()) {
                        const { uid } = phoneSnapshot.val();
                        if (!uid) throw new Error("Could not find user ID for this phone.");
                        
                        const userRef = ref(db, `users/${uid}`);
                        const userSnapshot = await get(userRef);
                        if(userSnapshot.exists()){
                            userEmail = userSnapshot.val().email;
                             if (!userEmail) throw new Error("No email associated with this phone number.");
                        } else {
                            throw new Error("User profile not found.");
                        }
                    } else {
                        throw new Error("User not found with this phone number.");
                    }
                }
                
                await signInWithEmailAndPassword(auth, userEmail, password);

            } catch (e) {
                console.error("Login Error:", e);
                let m = 'Login failed. Please check your credentials.';
                if (e.code === 'auth/invalid-credential' || e.code === 'auth/wrong-password' || e.code === 'auth/user-not-found' || e.message.includes("not found")) {
                    m = 'Invalid credentials. Please check your details and password.';
                }
                showStatusMessage(elements.loginStatusMessage, m, 'danger');
            } finally {
                showLoader(false);
            }
        }

        // MODIFIED handleSignup to use the new referral check method
        async function handleSignup() {
            const name = elements.signupNameInput.value.trim();
            const email = elements.signupEmailInput.value.trim();
            const phone = elements.signupPhoneInput.value.trim();
            const password = elements.signupPasswordInput.value;
            const confirmPassword = elements.signupConfirmPasswordInput.value;
            const referralCode = elements.signupReferralCodeInput.value.trim();

            if (!name || !email || !phone || !password) {
                showStatusMessage(elements.signupStatusMessage, 'All fields are required.', 'warning');
                return;
            }
             if (!/^[6-9][0-9]{9}$/.test(phone)) {
                showStatusMessage(elements.signupStatusMessage, 'Please enter a valid 10-digit Indian mobile number.', 'warning');
                return;
            }
            if (password !== confirmPassword) {
                showStatusMessage(elements.signupStatusMessage, 'Passwords do not match.', 'warning');
                return;
            }
            if (password.length < 6) {
                showStatusMessage(elements.signupStatusMessage, 'Password must be at least 6 characters long.', 'warning');
                return;
            }

            showLoader(true);
            clearStatusMessage(elements.signupStatusMessage);
            validatedReferrerInfo = null;

            try {
                const phoneToUidRef = ref(db, `phoneToUid/${phone}`);
                const phoneSnapshot = await get(phoneToUidRef);
                if (phoneSnapshot.exists()) {
                    throw new Error("This phone number is already registered.");
                }

                if (referralCode) {
                    const referralCodeRef = ref(db, `referralCodeToUid/${referralCode}`);
                    const snapshot = await get(referralCodeRef);

                    if (snapshot.exists()) {
                        const { uid: referrerId } = snapshot.val();
                        if (!referrerId) {
                             throw new Error("Referrer UID not found for the given code.");
                        }

                        const referrerProfileRef = ref(db, `users/${referrerId}`);
                        const referrerProfileSnapshot = await get(referrerProfileRef);

                        if (!referrerProfileSnapshot.exists()) {
                            throw new Error("Referrer profile does not exist.");
                        }
                        
                        const referrerProfile = referrerProfileSnapshot.val();

                        if (referrerProfile.email === email) {
                            showStatusMessage(elements.signupStatusMessage, "You cannot use your own referral code.", 'warning');
                            showLoader(false);
                            return;
                        }

                        validatedReferrerInfo = {
                            uid: referrerId,
                            displayName: referrerProfile.displayName
                        };
                        console.log("Valid referral code found for user:", validatedReferrerInfo.displayName);
                    } else {
                        showStatusMessage(elements.signupStatusMessage, "Invalid referral code. Please check it or leave it blank.", 'danger');
                        showLoader(false);
                        return;
                    }
                }
                await createUserWithEmailAndPassword(auth, email, password);
            } catch (e) {
                console.error("Signup Error:", e);
                let m = e.message;
                if (e.code === 'auth/email-already-in-use') {
                    m = 'This email address is already registered.';
                }
                showStatusMessage(elements.signupStatusMessage, m, 'danger');
                showLoader(false);
            }
        }
        
        async function handleForgotPassword() { 
            const email = elements.forgotEmailInput.value.trim(); 
            if (!email) { 
                showStatusMessage(elements.forgotStatusMessage, 'Please enter your registered email address.', 'warning'); 
                return; 
            } 
            showLoader(true); 
            clearStatusMessage(elements.forgotStatusMessage); 
            
            try { 
                await sendPasswordResetEmail(auth, email); 
                showStatusMessage(elements.forgotStatusMessage, 'Password reset link bhej diya gaya hai. Agar aapko email Inbox mein na dikhe, to kripya apna <strong>Spam folder</strong> zaroor check karein.', 'success', false); 
            } catch (e) { 
                console.error("Forgot Password Error:", e); 
                let m = 'Failed to send reset link.'; 
                if (e.code === 'auth/user-not-found') { 
                    m = 'No account found with this email address.'; 
                } 
                showStatusMessage(elements.forgotStatusMessage, m, 'danger'); 
            } finally { 
                showLoader(false); 
            } 
        }

        async function handleGoogleSignIn() { 
            const provider = new GoogleAuthProvider(); 
            showLoader(true); 
            try { 
                await signInWithPopup(auth, provider); 
            } catch (error) { 
                console.error("Google Sign-In Error:", error); 
                let message = "Could not sign in with Google. Please try again."; 
                if (error.code === 'auth/popup-closed-by-user') { 
                    message = "Sign-in window closed. Please try again."; 
                } else if (error.code === 'auth/account-exists-with-different-credential') { 
                    message = "An account already exists with this email. Please sign in using the original method."; 
                } 
                showStatusMessage(elements.loginStatusMessage, message, 'danger'); 
                showStatusMessage(elements.signupStatusMessage, message, 'danger'); 
            } finally {
                showLoader(false);
            } 
        }
        async function logoutUser() { if (!auth) return; try { showLoader(true); await signOut(auth); } catch (e) { console.error("Sign Out Error:", e); alert(`Logout failed: ${e.message}`); } finally { showLoader(false); } }
        
        function renderFilteredTournaments(){ if (!elements.tournamentsListContainer) return; const activeTab = document.querySelector('#tournaments-section .tab-item.active'); const status = activeTab ? activeTab.dataset.status : 'upcoming'; elements.tournamentsListContainer.innerHTML = ''; elements.noTournamentsMessage.style.display = 'none'; const filteredTournaments = Object.entries(currentGameTournamentsCache) .filter(([, t]) => { if (status === 'completed') { return ['completed', 'result', 'cancelled'].includes(t.status); } return t.status === status; }) .sort(([, tA], [, tB]) => (tB.startTime || 0) - (tA.startTime || 0)); if (filteredTournaments.length > 0) { filteredTournaments.forEach(([tId, t]) => { const card = createTournamentCardElement(tId, t); elements.tournamentsListContainer.appendChild(card); }); } else { elements.noTournamentsMessage.style.display = 'block'; let statusText = status; if (status === 'completed') statusText = 'results'; elements.noTournamentsMessage.textContent = `No ${statusText} tournaments found for this game.`; } }
        
        function loadTournamentsForGame(gameId, gameName) { 
            if (!elements.tournamentsSection) return; 
            currentTournamentGameId = gameId; 
            elements.tournamentTabs.forEach(t => t.classList.remove('active')); 
            document.querySelector('#tournaments-section .tab-item[data-status="upcoming"]')?.classList.add('active'); 
            elements.tournamentsListContainer.classList.add('placeholder-glow'); 
            elements.tournamentsListContainer.innerHTML = `<div class="tournament-card placeholder-glow mb-3"><span class="placeholder col-6"></span><span class="placeholder col-12 mt-2"></span><span class="placeholder col-10 mt-2"></span><div class="d-flex justify-content-between mt-3"><span class="placeholder col-4 h-30"></span><span class="placeholder col-4 h-30"></span></div></div>`; 
            elements.noTournamentsMessage.style.display = 'none'; 
            if (dbListeners['tournaments']) { const { path, func } = dbListeners['tournaments']; off(path, 'value', func); delete dbListeners['tournaments']; } 
            
            const tournamentsQuery = query(ref(db, 'tournaments'), orderByChild('gameId'), equalTo(gameId)); 
            
            const tournamentsListener = onValue(tournamentsQuery, (snapshot) => { 
                console.log(`Real-time update received for game: ${gameId}`); 
                currentGameTournamentsCache = snapshot.val() || {}; 
                // Removed auto-update logic here as requested
                removePlaceholders(elements.tournamentsListContainer); 
                renderFilteredTournaments(); 
            }, (error) => { 
                console.error("Tournament listener failed:", error); 
                removePlaceholders(elements.tournamentsListContainer); 
                elements.tournamentsListContainer.innerHTML = '<p class="text-danger text-center mt-4">Could not load tournaments.</p>'; 
                elements.noTournamentsMessage.style.display = 'none'; 
            }); 
            
            dbListeners['tournaments'] = { path: tournamentsQuery, func: tournamentsListener }; 
            showSection('tournaments-section'); 
        }
        
        function createTournamentCardElement(tId, t) {
            const card = document.createElement('div');
            card.className = 'tournament-card';
            card.dataset.tournamentId = tId;
            const eFee = t.entryFee || 0;
            const pkPrize = t.perKillPrize || 0;
            const pPool = t.prizePool || 0;
            const sTime = t.startTime ? new Date(t.startTime) : null;
            const sTimeLoc = sTime ? sTime.toLocaleString([], { dateStyle: 'short', timeStyle: 'short' }) : 'TBA';
            
            const regP = t.registeredPlayers || {};
            let totalRegisteredIndividualPlayers = 0;
            Object.values(regP).forEach(playerEntry => {
                totalRegisteredIndividualPlayers += (playerEntry.teamSize || 1);
            });

            const regC_individual = totalRegisteredIndividualPlayers;
            const maxP = t.maxPlayers || 0;
            const spotsL = maxP > 0 ? Math.max(0, maxP - regC_individual) : Infinity;

            const isF = maxP > 0 && spotsL <= 0;
            const isJ = currentUser && userProfile?.joinedTournaments?.[tId];
            const canJ = !isJ && !isF && t.status === 'upcoming';
            let timerTxt = t.status?.toUpperCase() || 'N/A';
            if (t.status === 'upcoming' && sTime) timerTxt = getTimeRemaining(t.startTime);
            else if (t.status === 'ongoing') timerTxt = 'LIVE';
            else if (t.status === 'completed' || t.status === 'result') timerTxt = 'ENDED';

            let spotsTxt = 'Unlimited Spots';
            let progP = 0;
            if (maxP > 0) {
                spotsTxt = `<span>${spotsL}</span> Spots Left (${regC_individual}/${maxP})`;
                progP = Math.min(100, (regC_individual / maxP) * 100);
            }
            
            let actBtn = '';
            let idPassBtn = '';
            if (isJ) {
                actBtn = `<button class="btn btn-custom btn-sm btn-joined" disabled><i class="fa-solid fa-circle-check"></i> Joined</button>`;
                if (t.status === 'ongoing' || (t.status === 'upcoming' && t.showIdPass && sTime && Date.now() > sTime.getTime() - 900000)) {
                    idPassBtn = `<button class="btn btn-custom btn-idpass w-100 mt-2 btn-sm" data-tournament-id="${tId}"><i class="fa-solid fa-key"></i> View ID & Pass</button>`;
                }
            } else if (canJ) {
                actBtn = `<button class="btn btn-custom btn-sm btn-custom-accent btn-join" data-tournament-id="${tId}" data-fee="${eFee}">₹${eFee} Join <i class="fa-solid fa-arrow-right"></i></button>`;
            } else {
                let disR = t.status !== 'upcoming' ? t.status?.toUpperCase() : (isF ? 'Full' : 'Closed');
                actBtn = `<button class="btn btn-custom btn-sm btn-disabled" disabled>${disR || 'N/A'}</button>`;
            }
            card.innerHTML = `<div class="tournament-card-header"><div class="tournament-card-tags">${t.mode ? `<span>${t.mode}</span>` : ''}${t.map ? `<span>${t.map}</span>` : ''}${t.tags ? (Array.isArray(t.tags) ? t.tags.map(tag => `<span>${tag}</span>`).join('') : Object.values(t.tags).map(tag => `<span>${tag}</span>`).join('')) : ''}</div><div class="tournament-card-timer">${timerTxt}</div></div><h3 class="tournament-card-title">${t.icon ? `<i class="${t.icon}"></i>` : '<i class="fa-solid fa-trophy text-accent"></i>'} ${t.name || 'Tournament'}</h3><p class="small text-secondary mb-2"><i class="fa-solid fa-calendar-alt"></i> ${sTimeLoc}</p><div class="tournament-card-info"><div class="info-item"><span>Prize Pool</span><strong><i class="fa-solid fa-trophy text-accent prize-icon"></i> ₹${pPool}</strong></div><div class="info-item"><span>Per Kill</span><strong>₹${pkPrize}</strong></div><div class="info-item"><span>Entry Fee</span><strong class="${eFee > 0 ? 'text-info' : ''}">${eFee > 0 ? `₹${eFee}` : 'Free'}</strong></div></div><div class="tournament-card-spots">${spotsTxt}${maxP > 0 ? `<div class="progress mt-1" style="height: 6px;"><div class="progress-bar" role="progressbar" style="width: ${progP}%"></div></div>` : ''}</div><div class="tournament-card-actions"><button class="btn btn-custom btn-custom-secondary btn-sm btn-details" data-tournament-id="${tId}">Details</button>${actBtn}</div>${idPassBtn}`;
            const jBtn = card.querySelector('.btn-join');
            if (jBtn) jBtn.addEventListener('click', handleJoinTournamentClick);
            const dBtn = card.querySelector('.btn-details');
            if (dBtn) dBtn.addEventListener('click', handleMatchDetailsClick);
            const ipBtn = card.querySelector('.btn-idpass');
            if (ipBtn) ipBtn.addEventListener('click', handleIdPasswordClick);

            if (currentUser && userProfile && (t.status === 'completed' || t.status === 'result')) {
                if (t.winners && t.winners[currentUser.uid]) {
                    const countedWins = userProfile.countedWins || {};
                    if (!countedWins[tId]) {
                        console.log(`Detected an uncounted win for tournament ${tId}. Updating stats.`);
                        const userRef = ref(db, `users/${currentUser.uid}`);
                        runTransaction(userRef, (profileData) => {
                            if (profileData) {
                                const wins = profileData.countedWins || {};
                                if (!wins[tId]) {
                                    profileData.wonMatches = (profileData.wonMatches || 0) + 1;
                                    if (!profileData.countedWins) {
                                        profileData.countedWins = {};
                                    }
                                    profileData.countedWins[tId] = true;
                                }
                            }
                            return profileData;
                        }).then(transactionResult => {
                            if (transactionResult.committed) {
                                console.log(`Stats for tournament ${tId} updated successfully.`);
                            }
                        }).catch(error => {
                            console.error(`Failed to update win stats for tournament ${tId}:`, error);
                        });
                    }
                }
            }
            return card;
        }

        async function loadMyContests() { if (!currentUser || !elements.myContestsList) { if(elements.myContestsList) removePlaceholders(elements.myContestsList); if(elements.myContestsList) elements.myContestsList.innerHTML = ''; if (elements.noContestsMessage) elements.noContestsMessage.style.display = 'block'; return; } const joinedIds = Object.keys(userProfile.joinedTournaments || {}); elements.myContestsList.classList.add('placeholder-glow'); elements.myContestsList.innerHTML = `<div class="tournament-card placeholder-glow mb-3"><span class="placeholder col-6"></span><span class="placeholder col-12 mt-2"></span><span class="placeholder col-10 mt-2"></span><div class="d-flex justify-content-between mt-3"><span class="placeholder col-4 h-30"></span><span class="placeholder col-4 h-30"></span></div></div>`; if (elements.noContestsMessage) elements.noContestsMessage.style.display = 'none'; if (joinedIds.length === 0) { removePlaceholders(elements.myContestsList); elements.myContestsList.innerHTML = ''; if (elements.noContestsMessage) elements.noContestsMessage.style.display = 'block'; return; } try { const contestPromises = joinedIds.map(id => get(ref(db, `tournaments/${id}`))); const snapshots = await Promise.all(contestPromises); removePlaceholders(elements.myContestsList); elements.myContestsList.innerHTML = ''; const contestCards = []; snapshots.forEach((snapshot, index) => { if (snapshot.exists()) { const t = snapshot.val(); if (t.status === 'upcoming' || t.status === 'ongoing') { const tId = joinedIds[index]; contestCards.push({ startTime: t.startTime || 0, card: createTournamentCardElement(tId, t) }); } } else { console.warn(`Joined tournament ${joinedIds[index]} not found.`); } }); contestCards.sort((a, b) => a.startTime - b.startTime); if (contestCards.length > 0) { contestCards.forEach(item => elements.myContestsList.appendChild(item.card)); } else if (elements.noContestsMessage) { elements.noContestsMessage.style.display = 'block'; elements.noContestsMessage.textContent = "No upcoming/ongoing joined contests."; } } catch (e) { console.error("My contests load failed:", e); removePlaceholders(elements.myContestsList); elements.myContestsList.innerHTML = '<p class="text-danger tc">Could not load contests.</p>'; } }
        function loadWalletData() { if (!currentUser) return; if (userProfile) { const balance = (userProfile.balance || 0); const winningCash = (userProfile.winningCash || 0); const bonusCash = (userProfile.bonusCash || 0); const formatCurrency = (amount) => `₹${amount.toFixed(2)}`; if (elements.walletTotalBalance) { elements.walletTotalBalance.textContent = formatCurrency(balance); removePlaceholders(elements.walletTotalBalance.closest('.placeholder-glow')); } if (elements.walletWinningCash) { elements.walletWinningCash.textContent = formatCurrency(winningCash); removePlaceholders(elements.walletWinningCash.closest('.placeholder-glow')); } if (elements.walletBonusCash) { elements.walletBonusCash.textContent = formatCurrency(bonusCash); removePlaceholders(elements.walletBonusCash.closest('.placeholder-glow')); } } loadRecentTransactions(); }
        function loadProfileData() { if (!currentUser) return; if (userProfile?.displayName) { populateUserInfo(currentUser, userProfile); } }
        
        function loadEarningsData() {
            if (!currentUser) return;
            if (typeof userProfile?.totalEarnings !== 'undefined') removePlaceholders(elements.earningsTotal?.closest('.placeholder-glow'));
            if (typeof userProfile?.referralEarnings !== 'undefined') removePlaceholders(elements.earningsReferral?.closest('.placeholder-glow'));
            loadTopEarners();
        }

        function createTopEarnerElement(user, rank) {
            const item = document.createElement('div');
            item.className = 'custom-card p-3 mb-2';
            const avatar = user.photoURL || `https://ui-avatars.com/api/?name=${encodeURIComponent(user.displayName || 'P')}&background=10002b&color=e000ff&bold=true`;
            const earnings = (user.totalEarnings || 0).toFixed(2);

            item.innerHTML = `
            <div class="d-flex justify-content-between align-items-center">
                <div class="d-flex align-items-center" style="min-width: 0;">
                    <span class="me-3 fw-bold fs-5" style="width: 25px; text-align: center; color: var(--text-secondary);">#${rank}</span>
                    <img src="${avatar}" alt="Avatar" style="width: 40px; height: 40px; border-radius: 50%; object-fit: cover; margin-right: 15px; border: 1px solid var(--border-color);">
                    <div style="overflow: hidden; text-overflow: ellipsis; white-space: nowrap;">
                        <div class="fw-bold" style="overflow: hidden; text-overflow: ellipsis;">${user.displayName || 'Anonymous'}</div>
                        <div class="small text-secondary">Total Winnings</div>
                    </div>
                </div>
                <div class="fw-bold fs-6 text-success" style="white-space: nowrap; margin-left: 10px;">₹${earnings}</div>
            </div>
            `;
            return item;
        }

        async function loadTopEarners() {
            const listEl = elements.topEarnersList;
            const noMessageEl = elements.noTopEarnersMessage;
            if (!listEl || !noMessageEl) return;

            listEl.classList.add('placeholder-glow');
            listEl.innerHTML = `
                <div class="custom-card p-3 mb-2 placeholder-glow"><div class="d-flex justify-content-between align-items-center"><div class="d-flex align-items-center"><span class="placeholder me-3" style="width: 40px; height: 40px; border-radius: 50%;"></span><div><span class="placeholder col-5 d-block" style="height: 16px;"></span><span class="placeholder col-8 d-block mt-1" style="height: 14px;"></span></div></div><span class="placeholder col-3" style="height: 20px;"></span></div></div>
                <div class="custom-card p-3 mb-2 placeholder-glow"><div class="d-flex justify-content-between align-items-center"><div class="d-flex align-items-center"><span class="placeholder me-3" style="width: 40px; height: 40px; border-radius: 50%;"></span><div><span class="placeholder col-5 d-block" style="height: 16px;"></span><span class="placeholder col-8 d-block mt-1" style="height: 14px;"></span></div></div><span class="placeholder col-3" style="height: 20px;"></span></div></div>
            `;
            noMessageEl.style.display = 'none';

            try {
                const usersRef = ref(db, 'users');
                const snapshot = await get(usersRef);

                removePlaceholders(listEl);
                listEl.innerHTML = '';

                if (snapshot.exists()) {
                    const allUsers = snapshot.val();
                    const earners = Object.values(allUsers)
                        .filter(user => user.totalEarnings && user.totalEarnings > 0)
                        .sort((a, b) => b.totalEarnings - a.totalEarnings)
                        .slice(0, 10);

                    if (earners.length > 0) {
                        noMessageEl.style.display = 'none';
                        earners.forEach((user, index) => {
                            const item = createTopEarnerElement(user, index + 1);
                            listEl.appendChild(item);
                        });
                    } else {
                        noMessageEl.style.display = 'block';
                    }
                } else {
                    noMessageEl.style.display = 'block';
                }

            } catch (error) {
                console.error("Error loading top earners:", error);
                removePlaceholders(listEl);
                listEl.innerHTML = '<p class="text-danger text-center">Could not load top earners.</p>';
            }
        }

        async function recordTransaction(userId, type, amount, description, details = {}) { if (!userId) return; const transactionRef = ref(db, `transactions/${userId}`); const newTransaction = { type, amount, description, timestamp: serverTimestamp(), ...details }; try { await push(transactionRef, newTransaction); } catch (e) { console.error("Transaction record failed:", e); } }

        function getTransactionDisplayDetails(transaction) {
            const amount = Number(transaction.amount) || 0;
            const isCredit = amount > 0;
            const absAmount = Math.abs(amount).toFixed(2);
            let description = transaction.description;
            let icon = 'fa-solid fa-receipt';

            const creditMessages = [
                `Credit: ₹${absAmount} from match winnings.`, `Received: ₹${absAmount} in your wallet.`, `₹${absAmount} has been credited to your wallet.`, `Added: ₹${absAmount} to your balance.`, `Deposit of ₹${absAmount} successful.`, `Your wallet has been topped up with ₹${absAmount}.`, `A credit of ₹${absAmount} has been added to your account.`, `Referral bonus of ₹${absAmount} received.`, `Refund of ₹${absAmount} processed successfully.`, `You have received a credit of ₹${absAmount}.`
            ];
            const debitMessages = [
                `Debit: ₹${absAmount} for tournament entry.`, `Paid: ₹${absAmount} for match fee.`, `Payment of ₹${absAmount} for joining a contest.`, `Withdrawal request for ₹${absAmount} is processing.`, `You sent a payment of ₹${absAmount}.`, `₹${absAmount} transferred from your wallet.`, `Your payout request of ₹${absAmount} is in progress.`, `Debit: ₹${absAmount} for contest fee.`, `A payment of ₹${absAmount} was made from your account.`, `₹${absAmount} sent from your wallet.`
            ];

            switch (transaction.type) {
                case 'add_money':
                    description = `Deposit of ₹${absAmount} successful.`;
                    icon = 'fa-solid fa-circle-down';
                    break;
                case 'admin_winning_add':
                case 'admin_bonus_add':
                    description = `₹${absAmount} has been successfully credited to your wallet.`;
                    icon = 'fa-solid fa-shield-check';
                    break;
                case 'winnings':
                    description = transaction.description || `Winnings of ₹${absAmount} have been added.`;
                    icon = 'fa-solid fa-trophy';
                    break;
                case 'referral_bonus':
                case 'referral_earning': // Added this case for consistency
                    description = transaction.description || `Referral bonus of ₹${absAmount} received.`;
                    icon = 'fa-solid fa-users';
                    break;
                case 'withdraw_request':
                    description = `Withdrawal request for ₹${absAmount} submitted.`;
                    icon = 'fa-solid fa-circle-up';
                    break;
                case 'withdraw_success':
                    description = `₹${absAmount} has been successfully transferred to your account.`;
                    icon = 'fa-solid fa-paper-plane';
                    break;
                case 'tournament_join':
                    description = transaction.description || `Paid ₹${absAmount} for match entry.`;
                    icon = 'fa-solid fa-gamepad';
                    break;
                case 'withdraw_failed_refund':
                case 'refund':
                    description = `Refund of ₹${absAmount} processed successfully.`;
                    icon = 'fa-solid fa-arrow-rotate-left';
                    break;
                default:
                    if (!description) {
                        description = isCredit ? creditMessages[Math.floor(Math.random() * creditMessages.length)] : debitMessages[Math.floor(Math.random() * debitMessages.length)];
                    }
                    if (isCredit) icon = 'fa-solid fa-plus-circle';
                    if (!isCredit) icon = 'fa-solid fa-minus-circle';
            }

            return {
                description: description,
                icon: icon,
                amountStr: `${isCredit ? '+' : '−'}₹${absAmount}`,
                amountClass: isCredit ? 'text-success' : 'text-danger'
            };
        }
        
        async function loadRecentTransactions() {
            if (!currentUser || !elements.recentTransactionsList) return;
            const limit = 5;
            elements.recentTransactionsList.innerHTML = '';
            elements.recentTransactionsList.classList.add('placeholder-glow');
            for (let i = 0; i < 3; i++) {
                elements.recentTransactionsList.innerHTML += `<div class="custom-card p-2 mb-2 placeholder-glow"><div class="d-flex justify-content-between"><span class="placeholder col-5" style="height: 16px;"></span><span class="placeholder col-3" style="height: 16px;"></span></div><div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div></div>`;
            }
            if (elements.noTransactionsMessage) {
                elements.noTransactionsMessage.style.display = 'block';
                elements.noTransactionsMessage.textContent = 'Loading transactions...';
            }
            try {
                const transRef = ref(db, `transactions/${currentUser.uid}`);
                const transQuery = query(transRef, limitToLast(limit));
                const s = await get(transQuery);
                const transactions = s.val() || {};
                const sortedT = Object.values(transactions)
                    .sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0));

                removePlaceholders(elements.recentTransactionsList);
                elements.recentTransactionsList.innerHTML = '';

                if (sortedT.length > 0) {
                    if (elements.noTransactionsMessage) elements.noTransactionsMessage.style.display = 'none';
                    sortedT.forEach(t => {
                        const item = document.createElement('div');
                        item.className = 'custom-card p-2 mb-2 d-flex justify-content-between align-items-center';
                        
                        const details = getTransactionDisplayDetails(t);
                        const time = t.timestamp ? new Date(t.timestamp).toLocaleString([], { dateStyle: 'short', timeStyle: 'short' }) : 'N/A';

                        item.innerHTML = `
                            <div>
                                <div class="small fw-bold">${details.description}</div>
                                <div class="small text-secondary">${time}</div>
                            </div>
                            <div class="fw-bold ${details.amountClass}">${details.amountStr}</div>
                        `;
                        elements.recentTransactionsList.appendChild(item);
                    });
                } else if (elements.noTransactionsMessage) {
                    elements.noTransactionsMessage.style.display = 'block';
                    elements.noTransactionsMessage.textContent = 'No recent transactions.';
                }
            } catch (e) {
                console.error("Transactions load failed:", e);
                removePlaceholders(elements.recentTransactionsList);
                elements.recentTransactionsList.innerHTML = '<p class="text-danger text-center">Could not load transactions.</p>';
                if (elements.noTransactionsMessage) elements.noTransactionsMessage.style.display = 'none';
            }
        }

        async function loadFullTransactionHistory() {
            if (!currentUser || !elements.fullTransactionsListEl) return;
            const listEl = elements.fullTransactionsListEl;
            const noMessageEl = elements.noFullTransactionsMessageEl;
            listEl.innerHTML = '';
            listEl.classList.add('placeholder-glow');
            for (let i = 0; i < 5; i++) {
                listEl.innerHTML += `<div class="custom-card p-2 mb-2 placeholder-glow"><div class="d-flex justify-content-between"><span class="placeholder col-5" style="height: 16px;"></span><span class="placeholder col-3" style="height: 16px;"></span></div><div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div></div>`;
            }
            if (noMessageEl) noMessageEl.style.display = 'none';
            try {
                const transRef = ref(db, `transactions/${currentUser.uid}`);
                const snapshot = await get(transRef);
                listEl.classList.remove('placeholder-glow');
                listEl.innerHTML = '';

                if (!snapshot.exists()) {
                    if (noMessageEl) {
                        noMessageEl.textContent = 'No transactions found.';
                        noMessageEl.style.display = 'block';
                    }
                    return;
                }
                const transactions = snapshot.val() || {};
                const sortedTransactions = Object.values(transactions)
                    .sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0));
                if (sortedTransactions.length > 0) {
                    if (noMessageEl) noMessageEl.style.display = 'none';
                    sortedTransactions.forEach(t => {
                        const item = document.createElement('div');
                        item.className = 'custom-card p-3 mb-2';
                        
                        const details = getTransactionDisplayDetails(t);
                        const timeStr = t.timestamp ? new Date(t.timestamp).toLocaleString([], { dateStyle: 'medium', timeStyle: 'short' }) : 'N/A';

                        item.innerHTML = `
                            <div class="d-flex justify-content-between align-items-center">
                                <div class="d-flex align-items-center" style="overflow: hidden; text-overflow: ellipsis;">
                                    <i class="fa-solid ${details.icon} me-3 fs-4 ${details.amountClass}"></i>
                                    <div>
                                        <div class="fw-bold">${details.description}</div>
                                        <div class="small text-secondary">${timeStr}</div>
                                    </div>
                                </div>
                                <div class="fw-bold fs-6 ${details.amountClass}" style="white-space: nowrap; margin-left: 10px;">${details.amountStr}</div>
                            </div>`;
                        listEl.appendChild(item);
                    });
                } else {
                    if (noMessageEl) {
                        noMessageEl.textContent = 'No transactions found.';
                        noMessageEl.style.display = 'block';
                    }
                }
            } catch (error) {
                console.error("Error loading full transaction history:", error);
                listEl.classList.remove('placeholder-glow');
                listEl.innerHTML = '<p class="text-danger text-center">Could not load transaction history. Please check your connection.</p>';
            }
        }
        
        async function loadFullEarningsHistory() {
            if (!currentUser || !elements.fullEarningsListEl) return;
            const listEl = elements.fullEarningsListEl;
            const noMessageEl = elements.noFullEarningsMessageEl;
            listEl.innerHTML = '';
            listEl.classList.add('placeholder-glow');
            for (let i = 0; i < 5; i++) {
                listEl.innerHTML += `<div class="custom-card p-2 mb-2 placeholder-glow"><div class="d-flex justify-content-between"><span class="placeholder col-5" style="height: 16px;"></span><span class="placeholder col-3" style="height: 16px;"></span></div><div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div></div>`;
            }
            if (noMessageEl) noMessageEl.style.display = 'none';
            try {
                const transRef = ref(db, `transactions/${currentUser.uid}`);
                const snapshot = await get(transRef);
                listEl.classList.remove('placeholder-glow');
                listEl.innerHTML = '';

                if (!snapshot.exists()) {
                    if (noMessageEl) {
                        noMessageEl.textContent = 'No earnings history found.';
                        noMessageEl.style.display = 'block';
                    }
                    return;
                }
                const transactions = snapshot.val() || {};
                const earningTypes = ['winnings', 'referral_bonus', 'referral_earning', 'admin_winning_add', 'admin_bonus_add'];
                const sortedEarnings = Object.values(transactions)
                    .filter(t => earningTypes.includes(t.type) && t.amount > 0)
                    .sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0)); 
                if (sortedEarnings.length > 0) {
                    if (noMessageEl) noMessageEl.style.display = 'none';
                    sortedEarnings.forEach(t => {
                        const item = document.createElement('div');
                        item.className = 'custom-card p-3 mb-2';

                        const amount = Number(t.amount) || 0;
                        const amountStr = `+₹${Math.abs(amount).toFixed(2)}`;
                        const timeStr = t.timestamp ? new Date(t.timestamp).toLocaleString([], { dateStyle: 'medium', timeStyle: 'short' }) : 'N/A';
                        
                        let icon = 'fa-solid fa-coins';
                        if (t.type?.includes('winnings')) icon = 'fa-solid fa-trophy';
                        if (t.type?.includes('referral')) icon = 'fa-solid fa-users';

                        const description = t.description || (t.type ? t.type.replace(/_/g, ' ').replace(/\b\w/g, l => l.toUpperCase()) : 'Earning');

                        item.innerHTML = `
                            <div class="d-flex justify-content-between align-items-center">
                                <div class="d-flex align-items-center" style="overflow: hidden; text-overflow: ellipsis;">
                                    <i class="${icon} me-3 fs-4 text-success"></i>
                                    <div>
                                        <div class="fw-bold">${description}</div>
                                        <div class="small text-secondary">${timeStr}</div>
                                    </div>
                                </div>
                                <div class="fw-bold fs-6 text-success" style="white-space: nowrap; margin-left: 10px;">${amountStr}</div>
                            </div>`;
                        listEl.appendChild(item);
                    });
                } else {
                    if (noMessageEl) {
                        noMessageEl.textContent = 'No earnings history found.';
                        noMessageEl.style.display = 'block';
                    }
                }
            } catch (error) {
                console.error("Error loading full earnings history:", error);
                listEl.classList.remove('placeholder-glow');
                listEl.innerHTML = '<p class="text-danger text-center">Could not load earnings history. Please check your connection.</p>';
            }
        }

        // ============================================================
        // FIX APPLIED HERE: Added 'approved', 'completed', 'paid' cases
        // ============================================================
        function createWithdrawalHistoryItemElement(request) {
            const item = document.createElement('div');
            item.className = 'custom-card p-3 mb-2';

            const amount = `₹${(request.amount || 0).toFixed(2)}`;
            const time = request.requestTimestamp ? new Date(request.requestTimestamp).toLocaleString() : 'N/A';
            const status = request.status || 'pending';
            const txnId = request.transactionId || null;

            let statusBadge;
            switch (status.toLowerCase()) {
                case 'successful':
                case 'success':
                case 'approved':   // Added this
                case 'completed':  // Added this
                case 'paid':       // Added this
                    statusBadge = `<span class="status-badge status-successful">Successful</span>`;
                    break;
                case 'rejected':
                case 'cancel':     // Added this
                case 'declined':   // Added this
                    statusBadge = `<span class="status-badge status-rejected">Rejected</span>`;
                    break;
                case 'pending':
                default:
                    statusBadge = `<span class="status-badge status-pending">Pending</span>`;
            }

            const txnIdHtml = txnId ? `<div class="txn-id"><strong>Transaction ID:</strong> ${txnId}</div>` : '';

            item.innerHTML = `
                <div class="d-flex justify-content-between align-items-center">
                    <div>
                        <strong class="fs-5 text-danger">${amount}</strong>
                        <div class="small text-secondary">${time}</div>
                    </div>
                    ${statusBadge}
                </div>
                ${txnIdHtml}
            `;
            return item;
        }

        function loadWithdrawalHistory() {
            if (!currentUser) return;
            if (dbListeners['withdrawals']) {
                const { path, func } = dbListeners['withdrawals'];
                off(path, 'value', func);
                delete dbListeners['withdrawals'];
            }
            
            const listEl = elements.withdrawalHistoryListEl;
            const noMessageEl = elements.noWithdrawalHistoryMessageEl;

            listEl.innerHTML = '';
            listEl.classList.add('placeholder-glow');
            for (let i = 0; i < 3; i++) {
                listEl.innerHTML += `<div class="custom-card p-2 mb-2 placeholder-glow"><div class="d-flex justify-content-between"><span class="placeholder col-4" style="height: 20px;"></span><span class="placeholder col-3" style="height: 20px; border-radius: 6px;"></span></div><div class="small text-secondary mt-1"><span class="placeholder col-6" style="height: 14px;"></span></div></div>`;
            }
            noMessageEl.style.display = 'none';

            const withdrawalsQuery = query(ref(db, 'withdrawals'), orderByChild('userId'), equalTo(currentUser.uid));

            const listener = onValue(withdrawalsQuery, (snapshot) => {
                listEl.classList.remove('placeholder-glow');
                listEl.innerHTML = '';

                if (!snapshot.exists()) {
                    noMessageEl.style.display = 'block';
                    return;
                }
                
                noMessageEl.style.display = 'none';
                const requests = [];
                snapshot.forEach(childSnapshot => {
                    requests.push(childSnapshot.val());
                });

                requests.sort((a, b) => (b.requestTimestamp || 0) - (a.requestTimestamp || 0));

                requests.forEach(request => {
                    const itemEl = createWithdrawalHistoryItemElement(request);
                    listEl.appendChild(itemEl);
                });

            }, (error) => {
                console.error("Error loading withdrawal history:", error);
                listEl.classList.remove('placeholder-glow');
                listEl.innerHTML = '<p class="text-danger text-center">Could not load withdrawal history.</p>';
            });

            dbListeners['withdrawals'] = { path: withdrawalsQuery, func: listener };
        }


        async function handleJoinTournamentClick(event) {
            if (!currentUser) {
                alert("Login to join.");
                showSection('login-section');
                return;
            }
            const btn = event.currentTarget;
            const tId = btn.dataset.tournamentId;
            const fee = parseFloat(btn.dataset.fee || 0);

            const tRef = ref(db, `tournaments/${tId}`);
            const tSnap = await get(tRef);
            if (!tSnap.exists()) {
                alert("Tournament not found.");
                return;
            }
            const tournamentData = tSnap.val();
            const mode = (tournamentData.mode || 'SOLO').toUpperCase();
            
            let multiplier = 1;
            if (mode === 'DUO') multiplier = 2;
            else if (mode === 'SQUAD') multiplier = 4;
            
            const totalFee = fee * multiplier;

            elements.joinTournamentIdInput.value = tId;
            elements.joinTournamentFeeInput.value = totalFee;
            elements.joinFeeDisplayEl.textContent = `₹${totalFee.toFixed(2)}`;
            elements.selectedSeatInput.value = '';
            clearStatusMessage(elements.joinTournamentStatusMessage);
            
            elements.joinTournamentForm.dataset.mode = mode;
            elements.joinTournamentForm.dataset.multiplier = multiplier;

            const playerInputsContainer = elements.joinPlayerInputsContainer;
            playerInputsContainer.innerHTML = '';
            for (let i = 1; i <= multiplier; i++) {
                let playerLabel = (multiplier > 1) ? `Player ${i}` : "Player";
                if (i === 1) playerLabel = (multiplier > 1) ? "Player 1 (You)" : "Your";

                const playerInputHTML = `
                    <div class="mb-2">
                        <label class="form-label small">${playerLabel} In-Game UID</label>
                        <input type="text" class="form-control form-control-sm" id="joinGameUidInput_${i}" placeholder="Enter Game User ID" required>
                    </div>
                    <div class="mb-3">
                        <label class="form-label small">${playerLabel} In-Game Name</label>
                        <input type="text" class="form-control form-control-sm" id="joinGameNameInput_${i}" placeholder="Enter Game Name" required>
                    </div>
                `;
                playerInputsContainer.insertAdjacentHTML('beforeend', playerInputHTML);
            }
            if(document.getElementById('joinGameUidInput_1')) document.getElementById('joinGameUidInput_1').value = userProfile.lastGameUid || '';
            if(document.getElementById('joinGameNameInput_1')) document.getElementById('joinGameNameInput_1').value = userProfile.lastGameName || '';

            const seatContainer = elements.seatSelectionContainer;
            seatContainer.innerHTML = '';
            const maxPlayers = tournamentData.maxPlayers || 100;
            const registeredPlayers = tournamentData.registeredPlayers || {};
            const occupiedSeats = new Set();
            
            Object.values(registeredPlayers).forEach(p => {
                if (p.seat) {
                    const start = p.seat;
                    const size = p.teamSize || 1;
                    for (let i = 0; i < size; i++) {
                        occupiedSeats.add(start + i);
                    }
                }
            });

            if (multiplier === 1) { 
                for (let i = 1; i <= maxPlayers; i++) {
                    const seatEl = document.createElement('div');
                    seatEl.className = 'seat';
                    seatEl.textContent = i;
                    seatEl.dataset.seatNumber = i;

                    if (occupiedSeats.has(i)) {
                        seatEl.classList.add('occupied');
                    } else {
                        seatEl.addEventListener('click', () => {
                            seatContainer.querySelectorAll('.seat.selected').forEach(s => s.classList.remove('selected'));
                            seatEl.classList.add('selected');
                            elements.selectedSeatInput.value = i;
                            clearStatusMessage(elements.joinTournamentStatusMessage);
                        });
                    }
                    seatContainer.appendChild(seatEl);
                }
            } else { 
                for (let i = 1; i <= maxPlayers; i += multiplier) {
                    const startSeat = i;
                    const endSeat = i + multiplier - 1;

                    if (endSeat > maxPlayers) continue;

                    const groupEl = document.createElement('div');
                    groupEl.className = 'seat-group';
                    groupEl.dataset.startSeat = startSeat;

                    const numberEl = document.createElement('div');
                    numberEl.className = 'group-number';
                    numberEl.textContent = `${(startSeat - 1) / multiplier + 1}.`;
                    groupEl.appendChild(numberEl);

                    let isBlockOccupied = false;
                    for (let j = startSeat; j <= endSeat; j++) {
                        if (occupiedSeats.has(j)) {
                            isBlockOccupied = true;
                        }
                        const seatEl = document.createElement('div');
                        seatEl.className = 'seat';
                        seatEl.textContent = j;
                        groupEl.appendChild(seatEl);
                    }

                    if (isBlockOccupied) {
                        groupEl.classList.add('occupied');
                    } else {
                        groupEl.addEventListener('click', () => {
                            seatContainer.querySelectorAll('.seat-group.selected').forEach(g => g.classList.remove('selected'));
                            seatContainer.querySelectorAll('.seat.selected').forEach(s => s.classList.remove('selected'));

                            groupEl.classList.add('selected');
                            groupEl.querySelectorAll('.seat').forEach(s => s.classList.add('selected'));
                            
                            elements.selectedSeatInput.value = startSeat;
                            clearStatusMessage(elements.joinTournamentStatusMessage);
                        });
                    }
                    seatContainer.appendChild(groupEl);
                }
            }
            elements.joinTournamentModalInstance.show();
        }

        async function handleConfirmJoin(event) {
            event.preventDefault();
            if (!currentUser) return;

            const btn = elements.confirmJoinBtn;
            const form = elements.joinTournamentForm;
            const tId = elements.joinTournamentIdInput.value;
            const totalFee = parseFloat(elements.joinTournamentFeeInput.value);
            const multiplier = parseInt(form.dataset.multiplier || 1);
            const selectedSeat = parseInt(elements.selectedSeatInput.value);

            const teamPlayers = [];
            for (let i = 1; i <= multiplier; i++) {
                const gameUidInput = form.querySelector(`#joinGameUidInput_${i}`);
                const gameNameInput = form.querySelector(`#joinGameNameInput_${i}`);
                const gameUid = gameUidInput ? gameUidInput.value.trim() : '';
                const gameName = gameNameInput ? gameNameInput.value.trim() : '';
                
                if (!gameUid || !gameName) {
                    showStatusMessage(elements.joinTournamentStatusMessage, `Please fill all details for Player ${i}.`, "warning");
                    return;
                }
                teamPlayers.push({ gameUid, gameName });
            }

            if (!selectedSeat) {
                showStatusMessage(elements.joinTournamentStatusMessage, "Please select your starting seat.", "warning");
                return;
            }

            btn.disabled = true;
            btn.innerHTML = '<span class="spinner-border spinner-border-sm"></span> Processing...';

            const userRef = ref(db, `users/${currentUser.uid}`);
            const tournamentRef = ref(db, `tournaments/${tId}`);

            let bonusToUse = 0;
            let mainBalanceDeduction = 0;

            try {
                await runTransaction(tournamentRef, (tournamentData) => {
                    if (!tournamentData) throw new Error("Tournament not found or has been removed.");
                    if (tournamentData.status !== 'upcoming') throw new Error("This tournament is no longer open for registration.");
                    if (tournamentData.registeredPlayers && tournamentData.registeredPlayers[currentUser.uid]) throw new Error("You have already joined this tournament.");
                    
                    const existingPlayers = tournamentData.registeredPlayers || {};
                    const occupiedSeatsInTx = new Set();
                    Object.values(existingPlayers).forEach(p => {
                        if (p.seat) {
                            const start = p.seat;
                            const size = p.teamSize || 1;
                            for (let i = 0; i < size; i++) {
                                occupiedSeatsInTx.add(start + i);
                            }
                        }
                    });

                    for (let i = 0; i < multiplier; i++) {
                        if (occupiedSeatsInTx.has(selectedSeat + i)) {
                            throw new Error(`Seat #${selectedSeat + i} was just taken. Please select another spot.`);
                        }
                    }

                    const currentPlayersCount = Array.from(occupiedSeatsInTx).length;
                    if (tournamentData.maxPlayers > 0 && (currentPlayersCount + multiplier > tournamentData.maxPlayers)) {
                        throw new Error("The tournament is full or does not have enough space for your team.");
                    }
                    
                    return tournamentData;
                });
                
                await runTransaction(userRef, (profileData) => {
                    if (!profileData) throw new Error("User profile not found.");
                    
                    const currentBonusBalance = profileData.bonusCash || 0;
                    const currentMainBalance = profileData.balance || 0;

                    // Calculate 1% of the total fee for bonus deduction
                    const potentialBonusDeduction = totalFee * 0.01;

                    bonusToUse = 0;
                    if (currentBonusBalance > 0) {
                        // Use the smaller value between available bonus and 1% of the fee
                        bonusToUse = Math.min(currentBonusBalance, potentialBonusDeduction);
                    }
                    
                    // The rest of the fee comes from the main balance
                    mainBalanceDeduction = totalFee - bonusToUse;

                    if (currentMainBalance < mainBalanceDeduction) {
                        throw new Error("Insufficient balance.");
                    }
                    
                    // Update balances
                    profileData.balance = currentMainBalance - mainBalanceDeduction;
                    profileData.bonusCash = currentBonusBalance - bonusToUse;

                    if (!profileData.joinedTournaments) profileData.joinedTournaments = {};
                    profileData.joinedTournaments[tId] = true;
                    profileData.lastGameUid = teamPlayers[0].gameUid;
                    profileData.lastGameName = teamPlayers[0].gameName;
                    profileData.totalMatches = (profileData.totalMatches || 0) + 1;

                    return profileData;
                });

                const playerDetails = {
                    joinedAt: serverTimestamp(),
                    seat: selectedSeat,
                    teamSize: multiplier,
                    displayName: userProfile.displayName,
                    uid: currentUser.uid,
                    team: teamPlayers
                };
                await update(ref(db, `tournaments/${tId}/registeredPlayers/${currentUser.uid}`), playerDetails);

                const tournamentName = currentGameTournamentsCache[tId]?.name || 'Tournament';
                const transactionDescription = `Joined: ${tournamentName}. Fee: ₹${totalFee.toFixed(2)} (₹${mainBalanceDeduction.toFixed(2)} from Main + ₹${bonusToUse.toFixed(2)} from Bonus).`;
                await recordTransaction(currentUser.uid, 'tournament_join', -totalFee, transactionDescription, { 
                    tournamentId: tId, 
                    seat: selectedSeat, 
                    teamSize: multiplier,
                    mainBalanceUsed: mainBalanceDeduction,
                    bonusUsed: bonusToUse
                });
                
                elements.joinTournamentModalInstance.hide();
                elements.joinSuccessModalInstance.show();

                if (currentSectionId === 'home-section') loadMyContests();
                if (currentSectionId === 'wallet-section') loadRecentTransactions();
                
                if (currentSectionId === 'tournaments-section') renderFilteredTournaments();


            } catch (error) {
                console.error("Join tournament failed:", error);
                showStatusMessage(elements.joinTournamentStatusMessage, `Failed to join: ${error.message}`, 'danger', false);
            } finally {
                btn.disabled = false;
                btn.innerHTML = 'Confirm & Pay';
            }
        }

        async function handleAddAmountClick() { if (!currentUser) { alert("Login first."); showSection('login-section'); return; } if (elements.addAmountModalInstance) { if (elements.paymentInstructions) { elements.paymentInstructions.style.display = 'none'; } elements.addAmountModalInstance.show(); } }
        function handleWithdrawClick() { if (!currentUser || !elements.withdrawModalInstance) return; const wc = userProfile.winningCash || 0; const minW = appSettings?.minWithdraw || 50; if (elements.minWithdrawAmountUpi) elements.minWithdrawAmountUpi.textContent = minW; if (elements.minWithdrawAmountBank) elements.minWithdrawAmountBank.textContent = minW; if (elements.withdrawModalBalance) elements.withdrawModalBalance.textContent = `₹${wc.toFixed(2)}`; elements.withdrawUpiAmountInput.value = ''; elements.withdrawUpiIdInput.value = userProfile.upiId || ''; elements.withdrawBankAmountInput.value = ''; elements.withdrawBankNameInput.value = userProfile.bankName || ''; elements.withdrawBankAccountInput.value = userProfile.bankAccount || ''; elements.withdrawBankReAccountInput.value = ''; elements.withdrawBankIfscInput.value = userProfile.bankIfsc || ''; clearStatusMessage(elements.withdrawStatusMessage); elements.withdrawModalInstance.show(); }
        async function submitWithdrawRequestHandler(btn, amount, methodDetails) { if (!currentUser) return; const wc = userProfile.winningCash || 0; const minW = appSettings?.minWithdraw || 50; clearStatusMessage(elements.withdrawStatusMessage); if (isNaN(amount) || amount <= 0) { showStatusMessage(elements.withdrawStatusMessage, 'Invalid amount.', 'warning'); return; } if (amount < minW) { showStatusMessage(elements.withdrawStatusMessage, `Minimum withdrawal is ₹${minW}.`, 'warning'); return; } if (amount > wc) { showStatusMessage(elements.withdrawStatusMessage, 'Insufficient winning balance.', 'warning'); return; } btn.disabled = true; btn.innerHTML = '<span class="spinner-border spinner-border-sm"></span> Sending...'; let transactionCommitted = false; const uRef = ref(db, `users/${currentUser.uid}`); try { const txResult = await runTransaction(uRef, (prof) => { if (prof) { const currentWinningCash = prof.winningCash || 0; const currentBalance = prof.balance || 0; if (currentWinningCash >= amount) { prof.winningCash = currentWinningCash - amount; prof.balance = currentBalance - amount; return prof; } else { throw new Error("Insufficient winning balance (Tx)."); } } else { throw new Error("Profile missing (Tx)."); } }); if (!txResult.committed) { throw new Error("Failed to update balance. Please try again."); } transactionCommitted = true; const wrRef = ref(db, 'withdrawals'); const newReq = { userId: currentUser.uid, userName: userProfile.displayName || currentUser.email, amount: amount, methodDetails: methodDetails, status: 'pending', requestTimestamp: serverTimestamp(), userEmail: currentUser.email || 'N/A' }; const newWithdrawalRef = await push(wrRef, newReq); await recordTransaction(currentUser.uid, 'withdraw_request', -amount, `A payout of ₹${amount} has been initiated.`, { withdrawalId: newWithdrawalRef.key, details: methodDetails }); 
 
             elements.withdrawModalInstance.hide();
             elements.withdrawalSuccessModalInstance.show();

         







            } catch (e) { console.error("Withdraw error:", e); showStatusMessage(elements.withdrawStatusMessage, `Error: ${e.message}`, 'danger'); if (transactionCommitted) { try { await runTransaction(uRef, (prof) => { if (prof) { prof.winningCash = (prof.winningCash || 0) + amount; prof.balance = (prof.balance || 0) + amount; } return prof; }); await recordTransaction(currentUser.uid, 'withdraw_failed_refund', amount, `Refund for failed withdrawal of ₹${amount}`); showStatusMessage(elements.withdrawStatusMessage, `Error: ${e.message}. Your balance has been refunded.`, 'danger', false); } catch (refundError) { console.error("CRITICAL: FAILED TO REFUND BALANCE!", refundError); showStatusMessage(elements.withdrawStatusMessage, `Error: ${e.message}. CRITICAL: Failed to refund amount! Contact support.`, 'danger', false); } } } finally { btn.disabled = false; btn.innerHTML = 'Submit Request'; } }
        async function handleMatchDetailsClick(event) { if (!elements.matchDetailsModalInstance) return; const tId = event.currentTarget.dataset.tournamentId; if (!tId) return; elements.matchDetailsModalTitle.textContent = 'Loading...'; elements.matchDetailsModalBody.innerHTML = '<div class="tc p-5"><div class="spinner-border spinner-border-sm"></div></div>'; elements.matchDetailsModalInstance.show(); try { const tRef = ref(db, `tournaments/${tId}`); const s = await get(tRef); if (s.exists()) { const t = s.val(); const gName = appSettings.games?.[t.gameId]?.name || t.gameId || 'N/A'; const sTimeLoc = t.startTime ? new Date(t.startTime).toLocaleString([], { dateStyle: 'medium', timeStyle: 'short'}) : 'TBA'; let pDistHTML = ''; if (t.prizeDistribution) { let fmtDist = ''; if (typeof t.prizeDistribution === 'object') { fmtDist = Object.entries(t.prizeDistribution).map(([rank, prize]) => `Rank ${rank}: ₹${prize}`).join('\n'); } else { fmtDist = String(t.prizeDistribution).replace(/\\n/g, '\n'); } pDistHTML = `<h5>Prize Distribution:</h5><pre>${fmtDist}</pre>`; } const desc = t.description || 'Standard rules apply.'; const fmtDesc = desc.replace(/\n/g, '<br>'); elements.matchDetailsModalTitle.textContent = t.name || 'Match Details'; elements.matchDetailsModalBody.innerHTML = `<p><strong>Game:</strong> ${gName}</p><p><strong>Mode:</strong> ${t.mode || 'N/A'}</p><p><strong>Map:</strong> ${t.map || 'N/A'}</p><p><strong>Starts:</strong> ${sTimeLoc}</p><hr><p><strong>Entry:</strong> ${t.entryFee > 0 ? `₹${t.entryFee}` : 'Free'}</p><p><strong>Prize:</strong> ₹${t.prizePool || 0}</p><p><strong>Per Kill:</strong> ₹${t.perKillPrize || 0}</p><p><strong>Max Players:</strong> ${t.maxPlayers > 0 ? t.maxPlayers : 'Unlimited'}</p><hr><h5>Rules:</h5><div style="white-space: pre-wrap; line-height: 1.6;">${fmtDesc}</div>${pDistHTML}`; } else elements.matchDetailsModalBody.innerHTML = '<p class="text-danger">Details not found.</p>'; } catch (e) { console.error("Details load failed:", e); elements.matchDetailsModalBody.innerHTML = '<p class="text-danger">Error loading details.</p>'; } }
        async function handleIdPasswordClick(event) { if (!elements.idPasswordModalInstance) return; const tId = event.currentTarget.dataset.tournamentId; if (!tId) return; if (!currentUser || !userProfile?.joinedTournaments?.[tId]) { alert("Join the tournament first or refresh the page."); return; } elements.roomIdDisplay.innerHTML = '<span class="placeholder col-6"></span>'; elements.roomPasswordDisplay.innerHTML = '<span class="placeholder col-6"></span>'; elements.idPasswordModalInstance.show(); try { const tournamentRef = ref(db, `tournaments/${tId}`); const s = await get(tournamentRef); removePlaceholders(elements.roomIdDisplay.closest('.placeholder-glow')); removePlaceholders(elements.roomPasswordDisplay.closest('.placeholder-glow')); if (s.exists()) { const tournamentData = s.val(); if (tournamentData.showIdPass) { elements.roomIdDisplay.textContent = tournamentData.roomId || 'Not updated yet'; elements.roomPasswordDisplay.textContent = tournamentData.roomPassword || 'Not updated yet'; } else { elements.roomIdDisplay.textContent = 'Hidden by Admin'; elements.roomPasswordDisplay.textContent = 'Hidden by Admin'; } } else { elements.roomIdDisplay.textContent = 'Not Found'; elements.roomPasswordDisplay.textContent = 'Not Found'; } } catch (e) { console.error("ID/Pass fetch error:", e); removePlaceholders(elements.roomIdDisplay.closest('.placeholder-glow')); removePlaceholders(elements.roomPasswordDisplay.closest('.placeholder-glow')); elements.roomIdDisplay.textContent = 'Error'; elements.roomPasswordDisplay.textContent = 'Error'; alert("Error loading ID/Password."); } }
        async function handlePolicyClick(event) { event.preventDefault(); const target = event.currentTarget; const policyType = target.dataset.policy; if (!policyType) return; if (policyType === 'refer') { if (!currentUser) { alert("Please log in to see your referral code."); return; } const refCode = userProfile.referralCode || 'N/A'; const refBonus = appSettings?.referralBonus || 0; const refDesc = appSettings?.referralDescription || `Get ₹${refBonus} when your friend joins using your code.`; const referralLink = `${window.location.origin}/?ref=${refCode}`; const modalBodyContent = ` <div class="text-center"> <h4>Refer Friends!</h4> <p class="text-secondary">Share your code and earn rewards!</p> <div class="my-4 p-3" style="background: var(--primary-bg); border-radius: 8px;"> <p class="small text-secondary mb-1">Your Code:</p> <h3 class="text-accent referral-code" id="referralCodeDisplay">${refCode}</h3> <div class="mt-3 d-flex justify-content-center gap-2"> <button class="btn btn-sm btn-custom btn-custom-secondary" id="copyReferralCodeBtn"> <i class="fa-solid fa-clipboard"></i> Copy Code </button> <button class="btn btn-sm btn-custom btn-custom-secondary" id="shareReferralLinkBtn"> <i class="fa-solid fa-share-alt"></i> Share Link </button> </div> </div> <p class="mt-3 small text-secondary">${refDesc}</p> </div>`; elements.policyModalTitle.textContent = 'Refer & Earn'; elements.policyModalBody.innerHTML = modalBodyContent; elements.policyModalInstance.show(); const copyCodeBtn = getElement('copyReferralCodeBtn'); const shareLinkBtn = getElement('shareReferralLinkBtn'); if (copyCodeBtn) { copyCodeBtn.onclick = () => { navigator.clipboard.writeText(refCode) .then(() => showToast("Referral code copied!")) .catch(err => console.error('Failed to copy code:', err)); }; } if (shareLinkBtn) { shareLinkBtn.onclick = async () => { const shareData = { title: 'Join and Earn Rewards! 🎁', text: `Use my referral code ${refCode} and earn rewards!`, url: referralLink }; try { if (navigator.share) { await navigator.share(shareData); } else { await navigator.clipboard.writeText(referralLink); showToast("Share not supported, referral link copied!"); } } catch (err) { console.log("Share failed, copying link instead.", err); await navigator.clipboard.writeText(referralLink); showToast("Referral link copied!"); } }; } return; } if (!elements.policyModalInstance) return; let title = '', modalBodyContent = '<div class="text-center p-5"><div class="spinner-border spinner-border-sm"></div></div>'; elements.policyModalBody.innerHTML = modalBodyContent; switch (policyType) { case 'privacy': title = 'Privacy Policy'; modalBodyContent = appSettings.policyPrivacy || 'Content not available.'; break; case 'terms': title = 'Terms and Conditions'; modalBodyContent = appSettings.policyTerms || 'Content not available.'; break; case 'refund': title = 'Refund and Cancellation'; modalBodyContent = appSettings.policyRefund || 'Content not available.'; break; case 'fairPlay': title = 'Fair Play Policy'; modalBodyContent = appSettings.policyFairPlay || 'Content not available.'; break; default: title = 'Info'; modalBodyContent = '<p>Content unavailable.</p>'; } elements.policyModalTitle.textContent = title; elements.policyModalBody.innerHTML = modalBodyContent.replace(/\n/g, '<br>'); elements.policyModalInstance.show(); }
        
        async function handleNotificationClick() {
            const isEnabled = localStorage.getItem('notificationsEnabled') !== 'false';
            if (!isEnabled) {
                showToast("Your notifications are currently turned off.");
                return;
            }
            await loadNotifications();
        }

        async function loadNotifications() {
            if (!currentUser || !elements.notificationModalInstance) return;
            const modalBody = elements.notificationModalBody;
            modalBody.innerHTML = '<div class="text-center p-5"><div class="spinner-border spinner-border-sm"></div></div>';
            elements.notificationModalInstance.show();

            try {
                const notifRef = ref(db, `notifications/${currentUser.uid}`);
                const snapshot = await get(query(notifRef, orderByChild('timestamp')));
                
                modalBody.innerHTML = '';
                if (!snapshot.exists()) {
                    modalBody.innerHTML = '<p class="text-secondary text-center p-4">You have no notifications.</p>';
                    return;
                }
                
                const allNotifications = [];
                const updates = {};
                snapshot.forEach(child => {
                    const notif = child.val();
                    notif.key = child.key; 
                    allNotifications.push(notif);
                    if (notif.read !== true) {
                        updates[`notifications/${currentUser.uid}/${child.key}/read`] = true;
                    }
                });

                // NEW LOGIC: Filter notifications older than 24 hours
                const twentyFourHoursAgo = Date.now() - (24 * 60 * 60 * 1000);
                const recentNotifications = allNotifications.filter(notif => notif.timestamp && notif.timestamp > twentyFourHoursAgo);

                // If no recent notifications are left after filtering, show a message.
                if (recentNotifications.length === 0) {
                    modalBody.innerHTML = '<p class="text-secondary text-center p-4">You have no new notifications from the last 24 hours.</p>';
                    // Even if we don't show them, we should mark them as read if they were unread.
                    if (Object.keys(updates).length > 0) {
                        await update(ref(db), updates);
                    }
                    return;
                }
                
                // NEW LOGIC: Sort by newest first (requirement 3)
                recentNotifications.reverse();

                recentNotifications.forEach(notif => {
                    const time = notif.timestamp ? new Date(notif.timestamp).toLocaleString() : '';
                    const item = document.createElement('div');
                    item.className = 'custom-card mb-2';
                    item.innerHTML = `
                        <h6 class="mb-1">${notif.title || 'Notification'}</h6>
                        <p class="small mb-2">${notif.message || ''}</p>
                        <p class="small text-secondary text-end mb-0">${time}</p>
                    `;
                    modalBody.appendChild(item);
                });

                // Mark the unread notifications as read in the database.
                if (Object.keys(updates).length > 0) {
                    await update(ref(db), updates);
                }

            } catch (e) {
                console.error("Error loading notifications:", e);
                modalBody.innerHTML = '<p class="text-danger text-center p-4">Could not load notifications.</p>';
            }
        }

        async function loadUnreadNotificationCount() { if (!currentUser || !elements.notificationBadge) return; if (localStorage.getItem('notificationsEnabled') === 'false') { elements.notificationBadge.style.display = 'none'; return; } try { const notifRef = query(ref(db, `notifications/${currentUser.uid}`), orderByChild('read'), equalTo(false)); const s = await get(notifRef); const count = s.size; if (count > 0) { elements.notificationBadge.textContent = count; elements.notificationBadge.style.display = 'flex'; } else { elements.notificationBadge.style.display = 'none'; } } catch(e) { console.error("Could not get notification count:", e); elements.notificationBadge.style.display = 'none'; } }
        
        function setupRealtimeListeners(uid) {
            if (!uid || !db || !currentUser) return;
            detachAllDbListeners();
            const uRef = ref(db, `users/${uid}`);
            const userListener = onValue(uRef, (s) => {
                if (currentUser && currentUser.uid === uid) {
                    if (s.exists()) {
                        userProfile = s.val();
                        populateUserInfo(currentUser, userProfile);
                        if (currentSectionId === 'home-section') loadMyContests();
                        if (currentSectionId === 'wallet-section') loadRecentTransactions();
                        if (currentSectionId === 'profile-section' && elements.editProfileContainer.style.display === 'none') loadProfileData();
                    } else {
                        alert("Account data missing or deleted. Logging out.");
                        logoutUser();
                    }
                }
            }, (e) => {
                console.error("Listener error (user profile):", e);
            });
            dbListeners['userProfile'] = { path: uRef, func: userListener };
        
            const notifRef = ref(db, `notifications/${uid}`);
            const notifListener = onValue(notifRef, () => {
                if (currentUser && currentUser.uid === uid) {
                    loadUnreadNotificationCount();
                }
            });
            dbListeners['notifications'] = { path: notifRef, func: notifListener };
        }
        
        function detachAllDbListeners() { console.log("Detaching all DB listeners...", Object.keys(dbListeners)); for (const key in dbListeners) { try { const { path, func } = dbListeners[key]; if (path && func) { off(path, 'value', func); } } catch (e) { console.error(`Error detaching listener for key "${key}":`, e); } } dbListeners = {}; if (chatMessagesListenerUnsubscribe) { chatMessagesListenerUnsubscribe(); chatMessagesListenerUnsubscribe = null; } }
        
        function applyTheme() { const savedTheme = localStorage.getItem('theme'); if (savedTheme === 'light') { document.body.classList.add('light-mode'); if (elements.themeSwitch) elements.themeSwitch.checked = false; } else { document.body.classList.remove('light-mode'); if (elements.themeSwitch) elements.themeSwitch.checked = true; } }
        
        function applyNotificationSetting() {
            const isEnabled = localStorage.getItem('notificationsEnabled') !== 'false';
            if (elements.notificationSwitch) {
                elements.notificationSwitch.checked = isEnabled;
            }
            updateNotificationIconVisibility();
        }

        function updateNotificationIconVisibility() {
            const isEnabled = localStorage.getItem('notificationsEnabled') !== 'false';
            const iconElement = elements.notificationBtn?.querySelector('i');

            if (iconElement) {
                if (isEnabled) {
                    iconElement.className = 'fa-solid fa-bell';
                } else {
                    iconElement.className = 'fa-solid fa-bell-slash';
                }
            }
        }

        function openChangePasswordModal(event) {
            event.preventDefault();
            if (elements.changePasswordModalInstance) {
                clearStatusMessage(elements.changePasswordStatusMessageEl);
                elements.changePasswordForm.reset();
                elements.changePasswordModalInstance.show();
            }
        }

        async function handleChangePassword(event) {
            event.preventDefault();
            const oldPassword = elements.oldPasswordInputEl.value;
            const newPassword = elements.newPasswordInputEl.value;
            const confirmPassword = elements.confirmPasswordInputEl.value;
            const statusEl = elements.changePasswordStatusMessageEl;
            const updateBtn = document.getElementById('updatePasswordBtnEl');

            if (!oldPassword || !newPassword || !confirmPassword) {
                showStatusMessage(statusEl, 'All fields are required.', 'warning');
                return;
            }
            if (newPassword !== confirmPassword) {
                showStatusMessage(statusEl, 'New passwords do not match.', 'warning');
                return;
            }
            if (newPassword.length < 6) {
                showStatusMessage(statusEl, 'New password must be at least 6 characters long.', 'warning');
                return;
            }

            const user = auth.currentUser;
            if (!user) {
                showStatusMessage(statusEl, 'You are not logged in.', 'danger');
                return;
            }

            updateBtn.disabled = true;
            updateBtn.innerHTML = '<span class="spinner-border spinner-border-sm"></span> Updating...';
            clearStatusMessage(statusEl);
            
            try {
                const credential = EmailAuthProvider.credential(user.email, oldPassword);
                await reauthenticateWithCredential(user, credential);
                await updatePassword(user, newPassword);
                showToast("Password updated successfully!");
                elements.changePasswordModalInstance.hide();
            } catch (error) {
                console.error("Password change error:", error);
                if (error.code === 'auth/wrong-password' || error.code === 'auth/invalid-credential') {
                    showStatusMessage(statusEl, 'Incorrect old password. Please try again.', 'danger');
                } else {
                    showStatusMessage(statusEl, 'An error occurred. Please try again later.', 'danger');
                }
            } finally {
                updateBtn.disabled = false;
                updateBtn.innerHTML = 'Update Password';
            }
        }
    </script>
    
</body>
</html>
