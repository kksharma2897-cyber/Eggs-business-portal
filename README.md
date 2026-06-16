<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Egg Business Portal | अंडा व्यापार पोर्टल</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Noto+Sans+Devanagari:wght@400;500;600;700&display=swap');

  :root {
    --yolk: #F5A623;
    --yolk-dark: #D4871A;
    --shell: #FFF8EE;
    --shell-mid: #FEF0D4;
    --brown: #5C3D1E;
    --brown-light: #8B6340;
    --green: #2E7D32;
    --green-light: #E8F5E9;
    --red: #C62828;
    --red-light: #FFEBEE;
    --blue: #1565C0;
    --blue-light: #E3F2FD;
    --orange-light: #FFF3E0;
    --gray: #616161;
    --gray-light: #F5F5F5;
    --white: #FFFFFF;
    --shadow: 0 2px 12px rgba(92,61,30,0.10);
    --shadow-lg: 0 8px 32px rgba(92,61,30,0.15);
    --radius: 14px;
    --radius-sm: 8px;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Inter', 'Noto Sans Devanagari', sans-serif;
    background: var(--shell);
    color: var(--brown);
    min-height: 100vh;
  }

  /* ===== BILINGUAL LABEL ===== */
  .bi { display: flex; flex-direction: column; line-height: 1.2; }
  .bi .en { font-size: 13px; font-weight: 600; color: var(--brown); }
  .bi .hi { font-size: 11px; font-weight: 400; color: var(--brown-light); font-family: 'Noto Sans Devanagari', sans-serif; }

  /* ===== PAGES ===== */
  .page { display: none; min-height: 100vh; }
  .page.active { display: block; }

  /* ===== LOGIN PAGE ===== */
  #loginPage {
    background: linear-gradient(135deg, #F5A623 0%, #D4871A 50%, #5C3D1E 100%);
    display: flex; align-items: center; justify-content: center;
    padding: 20px;
  }
  #loginPage.active { display: flex; }

  .login-card {
    background: var(--white);
    border-radius: 24px;
    padding: 40px 36px;
    width: 100%; max-width: 420px;
    box-shadow: var(--shadow-lg);
    text-align: center;
  }

  .login-logo {
    font-size: 56px; margin-bottom: 8px;
    animation: float 3s ease-in-out infinite;
  }
  @keyframes float {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }

  .login-title { font-size: 22px; font-weight: 700; color: var(--brown); margin-bottom: 4px; }
  .login-sub { font-size: 14px; color: var(--brown-light); font-family: 'Noto Sans Devanagari', sans-serif; margin-bottom: 28px; }

  .role-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 24px; }

  .role-btn {
    border: 2px solid var(--shell-mid);
    background: var(--shell);
    border-radius: 12px;
    padding: 16px 10px;
    cursor: pointer;
    transition: all 0.2s;
    text-align: center;
  }
  .role-btn:hover, .role-btn.selected {
    border-color: var(--yolk);
    background: var(--orange-light);
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(245,166,35,0.25);
  }
  .role-btn .icon { font-size: 28px; margin-bottom: 6px; }
  .role-btn .en { font-size: 12px; font-weight: 600; color: var(--brown); }
  .role-btn .hi { font-size: 10px; color: var(--brown-light); font-family: 'Noto Sans Devanagari', sans-serif; }

  .input-group { position: relative; margin-bottom: 16px; text-align: left; }
  .input-group label { display: block; margin-bottom: 6px; }
  .input-group input {
    width: 100%;
    padding: 12px 16px;
    border: 2px solid var(--shell-mid);
    border-radius: 10px;
    font-size: 14px;
    font-family: 'Inter', sans-serif;
    background: var(--shell);
    color: var(--brown);
    transition: border-color 0.2s;
  }
  .input-group input:focus { outline: none; border-color: var(--yolk); background: var(--white); }

  .btn-primary {
    width: 100%; padding: 14px;
    background: linear-gradient(135deg, var(--yolk), var(--yolk-dark));
    color: var(--white);
    border: none; border-radius: 12px;
    font-size: 15px; font-weight: 600;
    cursor: pointer; transition: all 0.2s;
    font-family: 'Inter', sans-serif;
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(245,166,35,0.4); }

  /* ===== MAIN APP ===== */
  #appPage { display: flex; flex-direction: column; }
  #appPage.active { display: flex; }

  /* TOP NAV */
  .topnav {
    background: var(--brown);
    padding: 0 20px;
    display: flex; align-items: center; justify-content: space-between;
    height: 60px;
    position: sticky; top: 0; z-index: 100;
    box-shadow: 0 2px 8px rgba(0,0,0,0.2);
  }
  .nav-brand { display: flex; align-items: center; gap: 10px; }
  .nav-brand .egg-icon { font-size: 24px; }
  .nav-brand .brand-text .en { font-size: 14px; font-weight: 700; color: var(--yolk); }
  .nav-brand .brand-text .hi { font-size: 10px; color: #ccc; font-family: 'Noto Sans Devanagari', sans-serif; }

  .nav-right { display: flex; align-items: center; gap: 12px; }
  .user-badge {
    background: rgba(245,166,35,0.15);
    border: 1px solid rgba(245,166,35,0.3);
    border-radius: 20px;
    padding: 4px 12px;
    font-size: 12px; color: var(--yolk); font-weight: 600;
  }
  .logout-btn {
    background: none; border: none; cursor: pointer;
    color: #ccc; font-size: 20px; transition: color 0.2s;
  }
  .logout-btn:hover { color: var(--yolk); }

  /* BOTTOM TABS */
  .bottom-tabs {
    position: fixed; bottom: 0; left: 0; right: 0;
    background: var(--white);
    border-top: 1px solid var(--shell-mid);
    display: flex;
    box-shadow: 0 -4px 16px rgba(92,61,30,0.10);
    z-index: 100;
  }
  .tab-btn {
    flex: 1; padding: 10px 4px;
    background: none; border: none;
    cursor: pointer; transition: all 0.2s;
    display: flex; flex-direction: column; align-items: center; gap: 2px;
  }
  .tab-btn .tab-icon { font-size: 22px; }
  .tab-btn .en { font-size: 10px; font-weight: 600; color: var(--gray); }
  .tab-btn .hi { font-size: 9px; color: #aaa; font-family: 'Noto Sans Devanagari', sans-serif; }
  .tab-btn.active .tab-icon { transform: translateY(-2px); }
  .tab-btn.active .en { color: var(--yolk-dark); }
  .tab-btn.active .hi { color: var(--yolk); }

  /* CONTENT AREA */
  .content { padding: 16px; padding-bottom: 80px; }

  /* ===== SECTION VIEWS ===== */
  .section-view { display: none; }
  .section-view.active { display: block; }

  /* ===== CARDS ===== */
  .card {
    background: var(--white);
    border-radius: var(--radius);
    padding: 18px;
    margin-bottom: 14px;
    box-shadow: var(--shadow);
  }
  .card-title {
    font-size: 13px; font-weight: 700;
    color: var(--brown-light);
    text-transform: uppercase; letter-spacing: 0.5px;
    margin-bottom: 14px;
    display: flex; align-items: center; gap: 6px;
  }

  /* ===== STAT GRID ===== */
  .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 14px; }
  .stat-box {
    border-radius: 12px; padding: 14px 12px; text-align: center;
  }
  .stat-box.green { background: var(--green-light); }
  .stat-box.red { background: var(--red-light); }
  .stat-box.blue { background: var(--blue-light); }
  .stat-box.orange { background: var(--orange-light); }
  .stat-num { font-size: 26px; font-weight: 700; line-height: 1; }
  .stat-box.green .stat-num { color: var(--green); }
  .stat-box.red .stat-num { color: var(--red); }
  .stat-box.blue .stat-num { color: var(--blue); }
  .stat-box.orange .stat-num { color: var(--yolk-dark); }
  .stat-label .en { font-size: 11px; font-weight: 600; color: var(--gray); margin-top: 4px; }
  .stat-label .hi { font-size: 10px; color: #aaa; font-family: 'Noto Sans Devanagari', sans-serif; }

  /* ===== TODAY RATE BANNER ===== */
  .rate-banner {
    background: linear-gradient(135deg, var(--yolk), var(--yolk-dark));
    border-radius: var(--radius);
    padding: 16px 20px;
    margin-bottom: 14px;
    display: flex; align-items: center; justify-content: space-between;
    color: var(--white);
  }
  .rate-banner .rate-left .en { font-size: 13px; font-weight: 600; opacity: 0.9; }
  .rate-banner .rate-left .hi { font-size: 11px; opacity: 0.75; font-family: 'Noto Sans Devanagari', sans-serif; }
  .rate-banner .rate-num { font-size: 28px; font-weight: 700; }
  .rate-banner .rate-sub { font-size: 12px; opacity: 0.85; }

  /* ===== PENDING ALERT ===== */
  .pending-alert {
    background: var(--red-light);
    border: 1px solid #FFCDD2;
    border-left: 4px solid var(--red);
    border-radius: var(--radius-sm);
    padding: 12px 16px;
    margin-bottom: 14px;
  }
  .pending-alert .en { font-size: 13px; font-weight: 600; color: var(--red); }
  .pending-alert .hi { font-size: 11px; color: #c62828cc; font-family: 'Noto Sans Devanagari', sans-serif; }

  /* ===== ORDER LIST ===== */
  .order-item {
    border: 1px solid var(--shell-mid);
    border-radius: var(--radius-sm);
    padding: 14px;
    margin-bottom: 10px;
    position: relative;
    background: var(--white);
  }
  .order-item.reserved { border-left: 4px solid var(--yolk); }
  .order-item.delivered { border-left: 4px solid var(--green); opacity: 0.75; }
  .order-item.pending-pay { border-left: 4px solid var(--red); }

  .order-header { display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 8px; }
  .order-name { font-size: 14px; font-weight: 700; color: var(--brown); }
  .order-receipt { font-size: 11px; color: var(--gray); }
  .order-meta { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 8px; }
  .tag {
    font-size: 11px; font-weight: 600;
    padding: 2px 8px; border-radius: 20px;
  }
  .tag.wholesale { background: var(--blue-light); color: var(--blue); }
  .tag.retail { background: var(--orange-light); color: var(--yolk-dark); }
  .tag.cash { background: var(--green-light); color: var(--green); }
  .tag.upi { background: #E8EAF6; color: #283593; }
  .tag.udhaar { background: var(--red-light); color: var(--red); }
  .tag.advance { background: #F3E5F5; color: #6A1B9A; }
  .tag.today { background: var(--green-light); color: var(--green); }
  .tag.tomorrow { background: var(--blue-light); color: var(--blue); }
  .tag.yesterday { background: var(--gray-light); color: var(--gray); }
  .tag.reserved-tag { background: var(--orange-light); color: var(--yolk-dark); }
  .tag.delivered-tag { background: var(--green-light); color: var(--green); }

  .order-footer { display: flex; justify-content: space-between; align-items: center; }
  .order-amount { font-size: 16px; font-weight: 700; color: var(--brown); }
  .order-trays { font-size: 12px; color: var(--gray); }

  .deliver-btn {
    background: var(--green); color: var(--white);
    border: none; border-radius: 8px;
    padding: 6px 14px; font-size: 12px; font-weight: 600;
    cursor: pointer; transition: all 0.2s;
  }
  .deliver-btn:hover { background: #1B5E20; }

  /* ===== STOCK PANEL ===== */
  .stock-panel {
    background: var(--brown);
    border-radius: var(--radius);
    padding: 16px;
    color: var(--white);
    margin-bottom: 14px;
  }
  .stock-panel-title { font-size: 12px; font-weight: 600; color: var(--yolk); opacity: 0.9; margin-bottom: 12px; text-transform: uppercase; letter-spacing: 0.5px; }
  .stock-row { display: flex; justify-content: space-between; align-items: center; padding: 8px 0; border-bottom: 1px solid rgba(255,255,255,0.08); }
  .stock-row:last-child { border-bottom: none; font-weight: 700; }
  .stock-row .label .en { font-size: 12px; color: #ddd; }
  .stock-row .label .hi { font-size: 10px; color: #aaa; font-family: 'Noto Sans Devanagari', sans-serif; }
  .stock-row .value { font-size: 18px; font-weight: 700; }
  .stock-row .value.green { color: #81C784; }
  .stock-row .value.red { color: #EF9A9A; }
  .stock-row .value.yellow { color: var(--yolk); }
  .stock-row .value.white { color: var(--white); }

  /* ===== FORM STYLES ===== */
  .form-section { margin-bottom: 20px; }
  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .field { margin-bottom: 14px; }
  .field label {
    display: block; margin-bottom: 6px;
    font-size: 12px;
  }
  .field input, .field select, .field textarea {
    width: 100%; padding: 11px 14px;
    border: 2px solid var(--shell-mid);
    border-radius: 10px;
    font-size: 14px; font-family: 'Inter', sans-serif;
    background: var(--shell); color: var(--brown);
    transition: border-color 0.2s;
  }
  .field input:focus, .field select:focus, .field textarea:focus {
    outline: none; border-color: var(--yolk); background: var(--white);
  }
  .field .hint { font-size: 11px; color: var(--gray); margin-top: 4px; }

  .calc-display {
    background: var(--orange-light);
    border: 2px solid var(--yolk);
    border-radius: 12px;
    padding: 14px 16px;
    margin-bottom: 14px;
    text-align: center;
  }
  .calc-display .total-label .en { font-size: 12px; color: var(--brown-light); }
  .calc-display .total-label .hi { font-size: 10px; color: var(--brown-light); font-family: 'Noto Sans Devanagari', sans-serif; }
  .calc-display .total-amount { font-size: 32px; font-weight: 700; color: var(--brown); }
  .calc-display .total-sub { font-size: 12px; color: var(--gray); margin-top: 4px; }

  .discount-row {
    display: flex; align-items: center; gap: 10px; margin-bottom: 14px;
  }
  .discount-row input { flex: 1; }
  .discount-row .discount-result { font-size: 13px; font-weight: 600; color: var(--red); white-space: nowrap; }

  /* DELIVERY DATE TOGGLE */
  .date-toggle { display: flex; gap: 8px; margin-bottom: 14px; }
  .date-option {
    flex: 1; padding: 10px 6px; text-align: center;
    border: 2px solid var(--shell-mid); border-radius: 10px;
    cursor: pointer; transition: all 0.2s; background: var(--shell);
  }
  .date-option:hover { border-color: var(--yolk); }
  .date-option.selected { border-color: var(--yolk); background: var(--orange-light); }
  .date-option .en { font-size: 12px; font-weight: 600; color: var(--brown); }
  .date-option .hi { font-size: 10px; color: var(--brown-light); font-family: 'Noto Sans Devanagari', sans-serif; }

  /* PAYMENT TYPE */
  .pay-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 14px; }
  .pay-option {
    padding: 10px; text-align: center;
    border: 2px solid var(--shell-mid); border-radius: 10px;
    cursor: pointer; transition: all 0.2s; background: var(--shell);
  }
  .pay-option .icon { font-size: 20px; margin-bottom: 4px; }
  .pay-option .en { font-size: 11px; font-weight: 600; color: var(--brown); }
  .pay-option .hi { font-size: 9px; color: var(--brown-light); font-family: 'Noto Sans Devanagari', sans-serif; }
  .pay-option.selected { border-color: var(--yolk); background: var(--orange-light); }

  /* STOCK WARNING */
  .stock-warning {
    background: var(--red-light); border: 2px solid #EF9A9A; border-radius: 10px;
    padding: 12px 14px; margin-bottom: 14px; display: none;
  }
  .stock-warning .en { font-size: 13px; font-weight: 600; color: var(--red); }
  .stock-warning .hi { font-size: 11px; color: var(--red); font-family: 'Noto Sans Devanagari', sans-serif; }

  /* ===== RECEIPT ===== */
  .receipt-card {
    border: 2px dashed var(--yolk);
    border-radius: var(--radius);
    padding: 20px;
    background: var(--white);
    margin-bottom: 14px;
  }
  .receipt-header { text-align: center; margin-bottom: 16px; padding-bottom: 14px; border-bottom: 1px solid var(--shell-mid); }
  .receipt-header .shop-name { font-size: 18px; font-weight: 700; color: var(--brown); }
  .receipt-header .shop-sub { font-size: 12px; color: var(--gray); font-family: 'Noto Sans Devanagari', sans-serif; }
  .receipt-row { display: flex; justify-content: space-between; padding: 6px 0; font-size: 13px; border-bottom: 1px solid var(--shell-mid); }
  .receipt-row:last-child { border-bottom: none; }
  .receipt-row .label { color: var(--gray); }
  .receipt-row .value { font-weight: 600; color: var(--brown); }
  .receipt-total { margin-top: 12px; padding-top: 12px; border-top: 2px solid var(--yolk); display: flex; justify-content: space-between; }
  .receipt-total .label { font-size: 14px; font-weight: 700; color: var(--brown); }
  .receipt-total .value { font-size: 18px; font-weight: 700; color: var(--yolk-dark); }
  .receipt-actions { display: flex; gap: 10px; }
  .receipt-actions button { flex: 1; padding: 12px; border-radius: 10px; font-size: 13px; font-weight: 600; cursor: pointer; border: none; transition: all 0.2s; }
  .wa-btn { background: #25D366; color: var(--white); }
  .wa-btn:hover { background: #1DA851; }
  .print-btn { background: var(--brown); color: var(--white); }
  .print-btn:hover { background: #3E2A10; }

  /* ===== RATE UPDATE ===== */
  .rate-update-card {
    background: linear-gradient(135deg, var(--brown), #3E2A10);
    border-radius: var(--radius);
    padding: 20px;
    color: var(--white);
    margin-bottom: 14px;
  }
  .rate-update-card .field label .en { color: #ddd; }
  .rate-update-card .field label .hi { color: #aaa; }
  .rate-update-card .field input {
    background: rgba(255,255,255,0.1);
    border-color: rgba(255,255,255,0.2);
    color: var(--white);
  }
  .rate-update-card .field input:focus { background: rgba(255,255,255,0.15); border-color: var(--yolk); }
  .rate-calc-display { background: rgba(245,166,35,0.15); border: 1px solid rgba(245,166,35,0.3); border-radius: 10px; padding: 12px; margin-bottom: 14px; text-align: center; }
  .rate-calc-display .tray-rate { font-size: 24px; font-weight: 700; color: var(--yolk); }
  .rate-calc-display .sub { font-size: 11px; color: #ccc; }

  .wa-share-msg {
    background: rgba(37,211,102,0.1);
    border: 1px solid rgba(37,211,102,0.3);
    border-radius: 10px; padding: 12px;
    font-size: 12px; color: #ddd;
    font-family: monospace;
    margin-bottom: 14px;
  }

  /* ===== BROKEN EGGS ===== */
  .broken-panel {
    background: var(--red-light);
    border: 2px solid #FFCDD2;
    border-radius: var(--radius);
    padding: 16px;
    margin-bottom: 14px;
  }
  .broken-progress { background: #FFCDD2; border-radius: 8px; height: 12px; margin: 10px 0; overflow: hidden; }
  .broken-bar { height: 100%; background: var(--red); border-radius: 8px; transition: width 0.3s; }
  .broken-count { font-size: 28px; font-weight: 700; color: var(--red); }
  .broken-label { font-size: 12px; color: var(--red); }

  /* ===== BUTTONS ===== */
  .btn-full {
    width: 100%; padding: 14px;
    border: none; border-radius: 12px;
    font-size: 14px; font-weight: 600;
    cursor: pointer; transition: all 0.2s;
    font-family: 'Inter', sans-serif;
  }
  .btn-full.primary { background: linear-gradient(135deg, var(--yolk), var(--yolk-dark)); color: var(--white); }
  .btn-full.primary:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(245,166,35,0.35); }
  .btn-full.green { background: var(--green); color: var(--white); margin-top: 8px; }
  .btn-full.danger { background: var(--red); color: var(--white); margin-top: 8px; }

  .btn-sm {
    padding: 8px 16px; border-radius: 8px;
    border: none; font-size: 12px; font-weight: 600;
    cursor: pointer; transition: all 0.2s;
  }
  .btn-sm.primary { background: var(--yolk); color: var(--white); }
  .btn-sm.outline { background: none; border: 2px solid var(--yolk); color: var(--yolk-dark); }

  /* ===== FILTER BAR ===== */
  .filter-bar { display: flex; gap: 8px; overflow-x: auto; padding-bottom: 4px; margin-bottom: 14px; }
  .filter-bar::-webkit-scrollbar { display: none; }
  .filter-chip {
    white-space: nowrap; padding: 6px 14px;
    border-radius: 20px; border: 2px solid var(--shell-mid);
    background: var(--white); font-size: 12px; font-weight: 600;
    cursor: pointer; color: var(--gray); transition: all 0.2s;
  }
  .filter-chip.active { border-color: var(--yolk); background: var(--orange-light); color: var(--yolk-dark); }

  /* ===== CUSTOMER PAGE ===== */
  .customer-welcome {
    background: linear-gradient(135deg, var(--yolk), var(--yolk-dark));
    border-radius: var(--radius); padding: 20px; color: var(--white); margin-bottom: 14px;
  }
  .customer-welcome h2 { font-size: 18px; font-weight: 700; margin-bottom: 4px; }
  .customer-welcome p { font-size: 13px; opacity: 0.9; font-family: 'Noto Sans Devanagari', sans-serif; }

  /* SECTION TITLE */
  .section-title { font-size: 16px; font-weight: 700; color: var(--brown); margin-bottom: 14px; display: flex; align-items: center; gap: 8px; }

  /* TOAST */
  .toast {
    position: fixed; bottom: 90px; left: 50%; transform: translateX(-50%);
    background: var(--brown); color: var(--white);
    padding: 12px 24px; border-radius: 24px;
    font-size: 13px; font-weight: 600;
    box-shadow: var(--shadow-lg);
    opacity: 0; transition: opacity 0.3s;
    z-index: 999; white-space: nowrap;
  }
  .toast.show { opacity: 1; }

  /* EMPTY STATE */
  .empty-state { text-align: center; padding: 40px 20px; color: var(--gray); }
  .empty-state .icon { font-size: 48px; margin-bottom: 12px; opacity: 0.5; }
  .empty-state p { font-size: 14px; }

  /* PRINT */
  @media print {
    body * { visibility: hidden; }
    .receipt-card, .receipt-card * { visibility: visible; }
    .receipt-card { position: fixed; top: 0; left: 0; width: 100%; }
    .receipt-actions { display: none; }
  }

  /* RESPONSIVE */
  @media (max-width: 380px) {
    .role-grid { grid-template-columns: 1fr 1fr; }
    .stat-grid { grid-template-columns: 1fr 1fr; }
    .form-row { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- ===== LOGIN PAGE ===== -->
<div id="loginPage" class="page active">
  <div class="login-card">
    <div class="login-logo">🥚</div>
    <div class="login-title">Egg Business Portal</div>
    <div class="login-sub">अंडा व्यापार पोर्टल</div>

    <div class="role-grid">
      <div class="role-btn" onclick="selectRole('superadmin')" id="role-superadmin">
        <div class="icon">🦸</div>
        <div class="en">Super Admin</div>
        <div class="hi">सुपर एडमिन</div>
      </div>
      <div class="role-btn" onclick="selectRole('father')" id="role-father">
        <div class="icon">👨</div>
        <div class="en">Owner</div>
        <div class="hi">मालिक (पापा)</div>
      </div>
      <div class="role-btn" onclick="selectRole('employee')" id="role-employee">
        <div class="icon">🧑‍💼</div>
        <div class="en">Employee</div>
        <div class="hi">कर्मचारी</div>
      </div>
      <div class="role-btn" onclick="selectRole('customer')" id="role-customer">
        <div class="icon">🛒</div>
        <div class="en">Customer</div>
        <div class="hi">ग्राहक</div>
      </div>
    </div>

    <div class="input-group">
      <label class="bi"><span class="en">Username / Phone</span><span class="hi">यूज़रनेम / फोन</span></label>
      <input type="text" id="loginUser" placeholder="Enter username">
    </div>
    <div class="input-group">
      <label class="bi"><span class="en">Password</span><span class="hi">पासवर्ड</span></label>
      <input type="password" id="loginPass" placeholder="••••••••">
    </div>

    <button class="btn-primary" onclick="doLogin()">
      Login &nbsp;|&nbsp; <span style="font-family:'Noto Sans Devanagari',sans-serif;font-size:13px;">लॉगिन करें</span>
    </button>
  </div>
</div>

<!-- ===== MAIN APP ===== -->
<div id="appPage" class="page">

  <!-- TOP NAV -->
  <div class="topnav">
    <div class="nav-brand">
      <div class="egg-icon">🥚</div>
      <div class="brand-text">
        <div class="en">Egg Portal</div>
        <div class="hi">अंडा पोर्टल</div>
      </div>
    </div>
    <div class="nav-right">
      <div class="user-badge" id="userBadge">Admin</div>
      <button class="logout-btn" onclick="doLogout()" title="Logout">⏻</button>
    </div>
  </div>

  <!-- CONTENT -->
  <div class="content">

    <!-- ===== DASHBOARD ===== -->
    <div id="dashboardView" class="section-view active">
      <div class="section-title">📊 Dashboard <span style="font-size:12px;color:var(--gray);font-weight:400;font-family:'Noto Sans Devanagari',sans-serif;">डैशबोर्ड</span></div>

      <!-- Today Rate Banner -->
      <div class="rate-banner">
        <div class="rate-left">
          <div class="en">🥚 Today's Rate</div>
          <div class="hi">आज का अंडा रेट</div>
        </div>
        <div>
          <div class="rate-num" id="dashRate">₹6.50</div>
          <div class="rate-sub" id="dashTrayRate">1 Tray = ₹195</div>
        </div>
      </div>

      <!-- Pending Alert -->
      <div class="pending-alert" id="pendingAlert">
        <div class="en">⚠️ 3 Udhaar Pending — ₹4,850 due</div>
        <div class="hi">3 उधार बाकी है — ₹4,850 लेना है</div>
      </div>

      <!-- Stats -->
      <div class="stat-grid">
        <div class="stat-box green">
          <div class="stat-num" id="statSold">80</div>
          <div class="stat-label"><div class="en">Trays Sold Today</div><div class="hi">आज बिकी ट्रे</div></div>
        </div>
        <div class="stat-box blue">
          <div class="stat-num" id="statReserved">30</div>
          <div class="stat-label"><div class="en">Reserved</div><div class="hi">रिज़र्व्ड</div></div>
        </div>
        <div class="stat-box orange">
          <div class="stat-num" id="statAmount">₹15.6k</div>
          <div class="stat-label"><div class="en">Today's Revenue</div><div class="hi">आज की कमाई</div></div>
        </div>
        <div class="stat-box red">
          <div class="stat-num" id="statUdhaar">₹4.8k</div>
          <div class="stat-label"><div class="en">Udhaar Pending</div><div class="hi">उधार बाकी</div></div>
        </div>
      </div>

      <!-- Stock Panel -->
      <div class="stock-panel">
        <div class="stock-panel-title">📦 Stock Summary | स्टॉक</div>
        <div class="stock-row">
          <div class="label"><div class="en">Yesterday Balance</div><div class="hi">कल का बचा हुआ</div></div>
          <div class="value yellow" id="stockOld">50</div>
        </div>
        <div class="stock-row">
          <div class="label"><div class="en">+ New Stock (Today)</div><div class="hi">+ आज आई ट्रे</div></div>
          <div class="value green" id="stockNew">+150</div>
        </div>
        <div class="stock-row">
          <div class="label"><div class="en">− Delivered</div><div class="hi">− डिलीवर हो गई</div></div>
          <div class="value red" id="stockDelivered">−80</div>
        </div>
        <div class="stock-row">
          <div class="label"><div class="en">🟡 Reserved (Pending)</div><div class="hi">🟡 रिज़र्व्ड (बाकी)</div></div>
          <div class="value yellow" id="stockReservedPanel">−30</div>
        </div>
        <div class="stock-row">
          <div class="label"><div class="en">❌ Broken Trays</div><div class="hi">❌ टूटे अंडे (ट्रे)</div></div>
          <div class="value red" id="stockBroken">−2</div>
        </div>
        <div class="stock-row" style="margin-top:8px;">
          <div class="label"><div class="en" style="color:var(--yolk);font-weight:700;">✅ Available Now</div><div class="hi" style="color:var(--yolk);">अभी उपलब्ध</div></div>
          <div class="value white" id="stockAvailable" style="font-size:24px;">88</div>
        </div>
      </div>

      <!-- Broken Eggs Entry -->
      <div class="broken-panel">
        <div class="card-title" style="color:var(--red);">❌ Broken Eggs | टूटे अंडे</div>
        <div style="display:flex;align-items:center;gap:12px;margin-bottom:10px;">
          <div>
            <div class="broken-count" id="brokenCount">15</div>
            <div class="broken-label en">eggs broken today</div>
            <div class="broken-label hi" style="font-family:'Noto Sans Devanagari',sans-serif;">आज टूटे अंडे</div>
          </div>
          <div style="flex:1;">
            <div style="font-size:11px;color:var(--red);margin-bottom:4px;">15 / 30 to next broken tray</div>
            <div class="broken-progress"><div class="broken-bar" id="brokenBar" style="width:50%"></div></div>
            <div style="font-size:11px;color:var(--red);margin-top:4px;" id="brokenTraysCount">0 trays broken | 0 ट्रे टूटी</div>
          </div>
        </div>
        <div style="display:flex;gap:8px;">
          <input type="number" id="brokenInput" placeholder="Add broken eggs..." style="flex:1;padding:10px 12px;border:2px solid #FFCDD2;border-radius:8px;font-size:13px;background:var(--white);color:var(--red);font-family:'Inter',sans-serif;">
          <button class="btn-sm primary" onclick="addBrokenEggs()" style="background:var(--red);">+ Add</button>
        </div>
      </div>

      <!-- Recent Orders -->
      <div class="section-title" style="margin-top:4px;">🧾 Recent Orders <span style="font-size:12px;color:var(--gray);font-weight:400;font-family:'Noto Sans Devanagari',sans-serif;">हाल के ऑर्डर</span></div>
      <div id="recentOrders">
        <!-- Sample orders -->
        <div class="order-item reserved">
          <div class="order-header">
            <div>
              <div class="order-name">Ramesh Sharma</div>
              <div class="order-receipt">#EGG-2025-001 &nbsp;|&nbsp; Today</div>
            </div>
            <button class="deliver-btn" onclick="markDelivered(this, 10)">✓ Delivered</button>
          </div>
          <div class="order-meta">
            <span class="tag wholesale">Wholesale</span>
            <span class="tag udhaar">Udhaar</span>
            <span class="tag reserved-tag">🟡 Reserved</span>
            <span class="tag today">Today</span>
          </div>
          <div class="order-footer">
            <div class="order-trays">10 Trays × ₹195</div>
            <div class="order-amount">₹1,950</div>
          </div>
        </div>
        <div class="order-item delivered">
          <div class="order-header">
            <div>
              <div class="order-name">Sunita Devi</div>
              <div class="order-receipt">#EGG-2025-002 &nbsp;|&nbsp; Today</div>
            </div>
            <span class="tag delivered-tag">✅ Delivered</span>
          </div>
          <div class="order-meta">
            <span class="tag retail">Retail</span>
            <span class="tag cash">Cash</span>
            <span class="tag delivered-tag">✅ Done</span>
          </div>
          <div class="order-footer">
            <div class="order-trays">5 Trays × ₹210 (−₹50 disc)</div>
            <div class="order-amount">₹1,000</div>
          </div>
        </div>
        <div class="order-item pending-pay">
          <div class="order-header">
            <div>
              <div class="order-name">Mohan Lal</div>
              <div class="order-receipt">#EGG-2025-003 &nbsp;|&nbsp; Tomorrow</div>
            </div>
            <button class="deliver-btn" onclick="markDelivered(this, 20)">✓ Delivered</button>
          </div>
          <div class="order-meta">
            <span class="tag wholesale">Wholesale</span>
            <span class="tag udhaar">Udhaar</span>
            <span class="tag reserved-tag">🟡 Reserved</span>
            <span class="tag tomorrow">Tomorrow</span>
          </div>
          <div class="order-footer">
            <div class="order-trays">20 Trays × ₹195</div>
            <div class="order-amount">₹3,900</div>
          </div>
        </div>
      </div>
    </div>

    <!-- ===== NEW ORDER ===== -->
    <div id="orderView" class="section-view">
      <div class="section-title">➕ New Order <span style="font-size:12px;color:var(--gray);font-weight:400;font-family:'Noto Sans Devanagari',sans-serif;">नया ऑर्डर</span></div>

      <!-- Stock Warning -->
      <div class="stock-warning" id="stockWarning">
        <div class="en">⚠️ Stock Warning! Only <span id="warnAvail">0</span> trays available</div>
        <div class="hi">स्टॉक कम है! सिर्फ <span id="warnAvail2">0</span> ट्रे बची हैं</div>
      </div>

      <!-- Customer Search -->
      <div class="card">
        <div class="card-title">👤 Customer | ग्राहक</div>
        <div class="field">
          <label class="bi"><span class="en">Search / Add Customer</span><span class="hi">ग्राहक खोजें / जोड़ें</span></label>
          <input type="text" id="custSearch" placeholder="Name or phone..." oninput="searchCustomer(this.value)">
        </div>
        <div id="custResults" style="display:none; border:1px solid var(--shell-mid);border-radius:8px;overflow:hidden;margin-bottom:10px;">
          <div onclick="selectCustomer('Ramesh Sharma','9876543210','Shimla')" style="padding:10px 12px;cursor:pointer;border-bottom:1px solid var(--shell-mid);font-size:13px;">
            <strong>Ramesh Sharma</strong> &nbsp;|&nbsp; 9876543210 &nbsp;|&nbsp; Shimla
          </div>
          <div onclick="selectCustomer('Sunita Devi','9765432100','Solan')" style="padding:10px 12px;cursor:pointer;font-size:13px;">
            <strong>Sunita Devi</strong> &nbsp;|&nbsp; 9765432100 &nbsp;|&nbsp; Solan
          </div>
        </div>

        <div id="newCustFields" style="display:none;">
          <div class="form-row">
            <div class="field">
              <label class="bi"><span class="en">Full Name</span><span class="hi">पूरा नाम</span></label>
              <input type="text" id="newCustName" placeholder="Customer name">
            </div>
            <div class="field">
              <label class="bi"><span class="en">Phone</span><span class="hi">फोन</span></label>
              <input type="tel" id="newCustPhone" placeholder="Mobile number">
            </div>
          </div>
          <div class="field">
            <label class="bi"><span class="en">Address / Delivery Location</span><span class="hi">पता / डिलीवरी जगह</span></label>
            <input type="text" id="newCustAddr" placeholder="Full address">
          </div>
        </div>

        <div id="selectedCust" style="display:none; background:var(--green-light);border-radius:8px;padding:10px 12px;">
          <div style="font-size:13px;font-weight:700;color:var(--green);" id="selCustName">Ramesh Sharma</div>
          <div style="font-size:11px;color:var(--gray);" id="selCustInfo">9876543210 | Shimla</div>
        </div>

        <button class="btn-sm outline" style="margin-top:8px;" onclick="toggleNewCust()">
          ➕ New Customer | नया ग्राहक
        </button>
      </div>

      <!-- Order Type -->
      <div class="card">
        <div class="card-title">🏷️ Order Type | ऑर्डर टाइप</div>
        <div style="display:flex;gap:10px;margin-bottom:0;">
          <div class="date-option selected" id="typeWhole" onclick="selectType('wholesale')" style="flex:1;">
            <div class="en">🏭 Wholesale</div>
            <div class="hi">थोक</div>
          </div>
          <div class="date-option" id="typeRetail" onclick="selectType('retail')" style="flex:1;">
            <div class="en">🛒 Retail</div>
            <div class="hi">पर्चून</div>
          </div>
        </div>
      </div>

      <!-- Quantity & Amount -->
      <div class="card">
        <div class="card-title">🥚 Quantity & Amount | मात्रा और रकम</div>
        <div class="form-row">
          <div class="field">
            <label class="bi"><span class="en">Trays</span><span class="hi">ट्रे</span></label>
            <input type="number" id="orderTrays" placeholder="0" oninput="calcAmount()">
          </div>
          <div class="field">
            <label class="bi"><span class="en">Rate/Egg (₹)</span><span class="hi">प्रति अंडा रेट</span></label>
            <input type="number" id="orderRate" placeholder="6.50" value="6.50" oninput="calcAmount()">
          </div>
        </div>

        <!-- Discount -->
        <label class="bi" style="margin-bottom:6px;"><span class="en">Discount (if any)</span><span class="hi">छूट (अगर हो)</span></label>
        <div class="discount-row">
          <input type="number" id="discountAmt" placeholder="₹0 discount" oninput="calcAmount()">
          <div class="discount-result" id="discResult">−₹0</div>
        </div>

        <div class="calc-display">
          <div class="total-label"><div class="en">Total Amount</div><div class="hi">कुल रकम</div></div>
          <div class="total-amount" id="orderTotal">₹0</div>
          <div class="total-sub" id="orderSub">0 Trays × ₹0 per tray</div>
        </div>
      </div>

      <!-- Delivery Date -->
      <div class="card">
        <div class="card-title">📅 Delivery Date | डिलीवरी तारीख</div>
        <div class="date-toggle">
          <div class="date-option" id="dateYesterday" onclick="selectDate('yesterday')">
            <div class="en">Yesterday</div><div class="hi">कल था</div>
          </div>
          <div class="date-option selected" id="dateToday" onclick="selectDate('today')">
            <div class="en">Today</div><div class="hi">आज</div>
          </div>
          <div class="date-option" id="dateTomorrow" onclick="selectDate('tomorrow')">
            <div class="en">Tomorrow</div><div class="hi">कल</div>
          </div>
        </div>
      </div>

      <!-- Payment Type -->
      <div class="card">
        <div class="card-title">💰 Payment Type | भुगतान</div>
        <div class="pay-grid">
          <div class="pay-option selected" id="payCash" onclick="selectPay('cash')">
            <div class="icon">💵</div>
            <div class="en">Cash</div>
            <div class="hi">नकद</div>
          </div>
          <div class="pay-option" id="payUpi" onclick="selectPay('upi')">
            <div class="icon">📱</div>
            <div class="en">UPI</div>
            <div class="hi">यूपीआई</div>
          </div>
          <div class="pay-option" id="payUdhaar" onclick="selectPay('udhaar')">
            <div class="icon">📒</div>
            <div class="en">Udhaar</div>
            <div class="hi">उधार</div>
          </div>
          <div class="pay-option" id="payAdvance" onclick="selectPay('advance')">
            <div class="icon">⬆️</div>
            <div class="en">Advance</div>
            <div class="hi">अग्रिम</div>
          </div>
        </div>
      </div>

      <button class="btn-full primary" onclick="placeOrder()">
        ✅ Place Order &nbsp;|&nbsp; <span style="font-family:'Noto Sans Devanagari',sans-serif;">ऑर्डर करें</span>
      </button>
    </div>

    <!-- ===== RECEIPT VIEW ===== -->
    <div id="receiptView" class="section-view">
      <div class="section-title">🧾 Receipt | रसीद</div>
      <div class="receipt-card" id="receiptContent">
        <div class="receipt-header">
          <div style="font-size:28px;margin-bottom:4px;">🥚</div>
          <div class="shop-name">Egg Business Portal</div>
          <div class="shop-sub">अंडा व्यापार पोर्टल</div>
          <div style="font-size:12px;color:var(--gray);margin-top:6px;" id="receiptDate">Date: —</div>
        </div>

        <div class="receipt-row"><span class="label">Receipt No.</span><span class="value" id="recNo">#EGG-2025-004</span></div>
        <div class="receipt-row"><span class="label">Customer</span><span class="value" id="recCust">—</span></div>
        <div class="receipt-row"><span class="label">Address</span><span class="value" id="recAddr">—</span></div>
        <div class="receipt-row"><span class="label">Phone</span><span class="value" id="recPhone">—</span></div>
        <div class="receipt-row"><span class="label">Type</span><span class="value" id="recType">Wholesale</span></div>
        <div class="receipt-row"><span class="label">Trays</span><span class="value" id="recTrays">—</span></div>
        <div class="receipt-row"><span class="label">Rate/Egg</span><span class="value" id="recRate">—</span></div>
        <div class="receipt-row"><span class="label">Rate/Tray</span><span class="value" id="recTrayRate">—</span></div>
        <div class="receipt-row" id="recDiscRow" style="display:none;"><span class="label">Discount</span><span class="value" style="color:var(--red);" id="recDisc">—</span></div>
        <div class="receipt-row"><span class="label">Delivery</span><span class="value" id="recDelivery">Today</span></div>
        <div class="receipt-row"><span class="label">Payment</span><span class="value" id="recPay">Cash</span></div>

        <div class="receipt-total">
          <span class="label">Total Amount</span>
          <span class="value" id="recTotal">₹0</span>
        </div>
      </div>

      <div class="receipt-actions">
        <button class="wa-btn" onclick="shareWhatsApp()">
          📱 WhatsApp
        </button>
        <button class="print-btn" onclick="window.print()">
          🖨️ Print | प्रिंट
        </button>
      </div>

      <button class="btn-full primary" style="margin-top:10px;" onclick="newOrder()">
        ➕ New Order | नया ऑर्डर
      </button>
    </div>

    <!-- ===== REPORTS ===== -->
    <div id="reportsView" class="section-view">
      <div class="section-title">📈 Reports | रिपोर्ट</div>

      <!-- Filter Bar -->
      <div class="filter-bar">
        <div class="filter-chip active" onclick="filterOrders('all',this)">All | सब</div>
        <div class="filter-chip" onclick="filterOrders('udhaar',this)">Udhaar | उधार</div>
        <div class="filter-chip" onclick="filterOrders('cash',this)">Cash | नकद</div>
        <div class="filter-chip" onclick="filterOrders('upi',this)">UPI</div>
        <div class="filter-chip" onclick="filterOrders('today',this)">Today | आज</div>
        <div class="filter-chip" onclick="filterOrders('tomorrow',this)">Tomorrow | कल</div>
        <div class="filter-chip" onclick="filterOrders('wholesale',this)">Wholesale | थोक</div>
        <div class="filter-chip" onclick="filterOrders('retail',this)">Retail | पर्चून</div>
      </div>

      <!-- Daily Summary -->
      <div class="card">
        <div class="card-title">📅 Today's Summary | आज की रिपोर्ट</div>
        <div class="receipt-row"><span class="label">Total Orders</span><span class="value">8</span></div>
        <div class="receipt-row"><span class="label">Trays Sold</span><span class="value">80</span></div>
        <div class="receipt-row"><span class="label">Total Revenue</span><span class="value" style="color:var(--green);">₹15,600</span></div>
        <div class="receipt-row"><span class="label">Cash Received</span><span class="value">₹8,400</span></div>
        <div class="receipt-row"><span class="label">UPI Received</span><span class="value">₹2,350</span></div>
        <div class="receipt-row"><span class="label" style="color:var(--red);">Udhaar Pending</span><span class="value" style="color:var(--red);">₹4,850</span></div>
        <div class="receipt-row"><span class="label">Broken Trays</span><span class="value" style="color:var(--red);">2</span></div>
      </div>

      <!-- Orders list filtered -->
      <div id="filteredOrders">
        <div class="order-item reserved">
          <div class="order-header"><div><div class="order-name">Ramesh Sharma</div><div class="order-receipt">#EGG-2025-001 | Today</div></div></div>
          <div class="order-meta"><span class="tag wholesale">Wholesale</span><span class="tag udhaar">Udhaar</span><span class="tag today">Today</span></div>
          <div class="order-footer"><div class="order-trays">10 Trays</div><div class="order-amount">₹1,950</div></div>
        </div>
        <div class="order-item delivered">
          <div class="order-header"><div><div class="order-name">Sunita Devi</div><div class="order-receipt">#EGG-2025-002 | Today</div></div></div>
          <div class="order-meta"><span class="tag retail">Retail</span><span class="tag cash">Cash</span></div>
          <div class="order-footer"><div class="order-trays">5 Trays</div><div class="order-amount">₹1,000</div></div>
        </div>
      </div>
    </div>

    <!-- ===== RATE UPDATE (Admin) ===== -->
    <div id="rateView" class="section-view">
      <div class="section-title">💰 Rate Update | रेट अपडेट</div>

      <div class="rate-update-card">
        <div style="font-size:14px;font-weight:700;color:var(--yolk);margin-bottom:16px;">🥚 Set Today's Rate | आज का रेट सेट करें</div>

        <div class="field">
          <label class="bi"><span class="en">Purchase Rate (per egg)</span><span class="hi">खरीद का रेट (प्रति अंडा)</span></label>
          <input type="number" id="purchaseRate" placeholder="5.00" oninput="calcFinalRate()">
        </div>
        <div class="field">
          <label class="bi"><span class="en">Transport Cost (per egg)</span><span class="hi">ट्रक भाड़ा (प्रति अंडा)</span></label>
          <input type="number" id="transportCost" placeholder="0.10" oninput="calcFinalRate()">
        </div>
        <div class="field">
          <label class="bi"><span class="en">Your Margin (per egg)</span><span class="hi">आपका मुनाफा (प्रति अंडा)</span></label>
          <input type="number" id="marginAmt" placeholder="0.50" oninput="calcFinalRate()">
        </div>
        <div class="field">
          <label class="bi"><span class="en">Delivery Charge (per egg)</span><span class="hi">डिलीवरी चार्ज (प्रति अंडा)</span></label>
          <input type="number" id="deliveryCharge" placeholder="0.20" oninput="calcFinalRate()">
        </div>

        <div class="rate-calc-display">
          <div style="font-size:11px;color:#aaa;margin-bottom:4px;">Final Rate Per Egg | प्रति अंडा अंतिम रेट</div>
          <div class="tray-rate" id="finalEggRate">₹5.80</div>
          <div class="sub">1 Tray (30 eggs) = <strong id="finalTrayRate" style="color:var(--yolk);">₹174</strong></div>
        </div>

        <div style="font-size:12px;color:#ccc;margin-bottom:8px;">📱 WhatsApp Message Preview:</div>
        <div class="wa-share-msg" id="waPreview">
🥚 Aaj ka Egg Rate 🥚
1 Anda = ₹5.80
1 Tray (30 Ande) = ₹174

Order ke liye sampark karein 📞</div>

        <button class="btn-full primary" onclick="updateRate()" style="margin-top:4px;">
          ✅ Update Rate | रेट अपडेट करें
        </button>
        <button class="btn-full" style="background:#25D366;color:white;margin-top:8px;" onclick="copyWaMessage()">
          📱 Copy WhatsApp Message | कॉपी करें
        </button>
      </div>

      <!-- Add Stock -->
      <div class="card">
        <div class="card-title">🚛 Add New Stock | नई ट्रे जोड़ें</div>
        <div class="field">
          <label class="bi"><span class="en">Trays Received Today</span><span class="hi">आज आई ट्रे</span></label>
          <input type="number" id="newStock" placeholder="Number of trays...">
        </div>
        <button class="btn-full primary" onclick="addStock()">
          ➕ Add to Stock | स्टॉक जोड़ें
        </button>
      </div>
    </div>

    <!-- ===== CUSTOMER VIEW ===== -->
    <div id="customerView" class="section-view">
      <div class="customer-welcome">
        <h2>Welcome! 🥚 नमस्ते!</h2>
        <p>ताज़ा अंडे, सही दाम पर</p>
      </div>

      <!-- Today Rate -->
      <div class="rate-banner" style="margin-bottom:14px;">
        <div class="rate-left">
          <div class="en">🥚 Today's Rate</div>
          <div class="hi">आज का रेट</div>
        </div>
        <div>
          <div class="rate-num">₹6.50</div>
          <div class="rate-sub">1 Tray = ₹195</div>
        </div>
      </div>

      <!-- Quick Order -->
      <div class="card">
        <div class="card-title">📦 Place Order | ऑर्डर करें</div>
        <div class="field">
          <label class="bi"><span class="en">Number of Trays</span><span class="hi">कितनी ट्रे चाहिए</span></label>
          <input type="number" id="custTrays" placeholder="1" oninput="custCalc()">
        </div>
        <div class="date-toggle">
          <div class="date-option selected" id="custToday" onclick="custDate('today')">
            <div class="en">Today</div><div class="hi">आज</div>
          </div>
          <div class="date-option" id="custTomorrow" onclick="custDate('tomorrow')">
            <div class="en">Tomorrow</div><div class="hi">कल</div>
          </div>
        </div>
        <div class="calc-display" style="margin-bottom:14px;">
          <div class="total-label"><div class="en">Your Total</div><div class="hi">आपकी कुल रकम</div></div>
          <div class="total-amount" id="custTotal">₹0</div>
        </div>
        <button class="btn-full primary" onclick="custPlaceOrder()">
          📦 Place Order | ऑर्डर करें
        </button>
      </div>

      <!-- My Orders -->
      <div class="section-title">📋 My Orders | मेरे ऑर्डर</div>
      <div class="order-item reserved">
        <div class="order-header"><div><div class="order-name">Order #EGG-2025-001</div><div class="order-receipt">Today | आज</div></div><span class="tag reserved-tag">🟡 Pending</span></div>
        <div class="order-footer"><div class="order-trays">10 Trays</div><div class="order-amount">₹1,950</div></div>
      </div>
      <div class="order-item delivered">
        <div class="order-header"><div><div class="order-name">Order #EGG-2025-000</div><div class="order-receipt">Yesterday</div></div><span class="tag delivered-tag">✅ Delivered</span></div>
        <div class="order-footer"><div class="order-trays">5 Trays</div><div class="order-amount">₹975</div></div>
      </div>
    </div>

  </div><!-- /content -->

  <!-- BOTTOM TABS -->
  <div class="bottom-tabs" id="bottomTabs">
    <button class="tab-btn active" id="tab-dashboard" onclick="showTab('dashboard')">
      <div class="tab-icon">📊</div>
      <div class="en">Dashboard</div>
      <div class="hi">डैशबोर्ड</div>
    </button>
    <button class="tab-btn" id="tab-order" onclick="showTab('order')">
      <div class="tab-icon">➕</div>
      <div class="en">New Order</div>
      <div class="hi">ऑर्डर</div>
    </button>
    <button class="tab-btn" id="tab-reports" onclick="showTab('reports')">
      <div class="tab-icon">📈</div>
      <div class="en">Reports</div>
      <div class="hi">रिपोर्ट</div>
    </button>
    <button class="tab-btn" id="tab-rate" onclick="showTab('rate')">
      <div class="tab-icon">💰</div>
      <div class="en">Rate</div>
      <div class="hi">रेट</div>
    </button>
  </div>

</div><!-- /appPage -->

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
// ===== STATE =====
let currentRole = null;
let selectedDelivDate = 'today';
let selectedPayType = 'cash';
let selectedOrderType = 'wholesale';
let custSelectedDate = 'today';
let brokenEggsCount = 15;
let brokenTrays = 0;
let receiptCounter = 4;
let currentOrder = {};
let availableStock = 88;

const DEMO_USERS = {
  superadmin: { user: 'admin', pass: '1234', name: 'Super Admin' },
  father:     { user: 'papa',  pass: '5678', name: 'Owner (Papa)' },
  employee:   { user: 'emp',   pass: 'emp1', name: 'Employee' },
  customer:   { user: 'cust',  pass: 'cust1',name: 'Customer' }
};

// ===== LOGIN =====
function selectRole(role) {
  currentRole = role;
  document.querySelectorAll('.role-btn').forEach(b => b.classList.remove('selected'));
  document.getElementById('role-' + role).classList.add('selected');
}

function doLogin() {
  if (!currentRole) { showToast('⚠️ Please select role | भूमिका चुनें'); return; }
  const u = document.getElementById('loginUser').value.trim();
  const p = document.getElementById('loginPass').value.trim();
  const demo = DEMO_USERS[currentRole];

  if (u === demo.user && p === demo.pass) {
    document.getElementById('loginPage').classList.remove('active');
    document.getElementById('appPage').classList.add('active');
    document.getElementById('userBadge').textContent = demo.name;
    setupRole(currentRole);
    showToast('✅ Welcome ' + demo.name);
  } else {
    showToast('❌ Wrong credentials | गलत पासवर्ड');
  }
}

function setupRole(role) {
  const tabs = document.getElementById('bottomTabs');
  if (role === 'customer') {
    tabs.innerHTML = `
      <button class="tab-btn active" id="tab-dashboard" onclick="showTab('customerHome')">
        <div class="tab-icon">🏠</div><div class="en">Home</div><div class="hi">होम</div>
      </button>
      <button class="tab-btn" id="tab-order" onclick="showTab('order')">
        <div class="tab-icon">➕</div><div class="en">Order</div><div class="hi">ऑर्डर</div>
      </button>`;
    showSection('customerView');
  } else if (role === 'employee') {
    document.getElementById('tab-rate').style.display = 'none';
    showSection('dashboardView');
  } else {
    showSection('dashboardView');
  }
}

function doLogout() {
  document.getElementById('appPage').classList.remove('active');
  document.getElementById('loginPage').classList.add('active');
  currentRole = null;
  document.querySelectorAll('.role-btn').forEach(b => b.classList.remove('selected'));
  document.getElementById('loginUser').value = '';
  document.getElementById('loginPass').value = '';
  // Reset tabs
  document.getElementById('bottomTabs').innerHTML = `
    <button class="tab-btn active" id="tab-dashboard" onclick="showTab('dashboard')">
      <div class="tab-icon">📊</div><div class="en">Dashboard</div><div class="hi">डैशबोर्ड</div>
    </button>
    <button class="tab-btn" id="tab-order" onclick="showTab('order')">
      <div class="tab-icon">➕</div><div class="en">New Order</div><div class="hi">ऑर्डर</div>
    </button>
    <button class="tab-btn" id="tab-reports" onclick="showTab('reports')">
      <div class="tab-icon">📈</div><div class="en">Reports</div><div class="hi">रिपोर्ट</div>
    </button>
    <button class="tab-btn" id="tab-rate" onclick="showTab('rate')">
      <div class="tab-icon">💰</div><div class="en">Rate</div><div class="hi">रेट</div>
    </button>`;
}

// ===== TABS =====
function showTab(tab) {
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  const el = document.getElementById('tab-' + tab);
  if (el) el.classList.add('active');

  const map = {
    dashboard: 'dashboardView',
    order: 'orderView',
    reports: 'reportsView',
    rate: 'rateView',
    customerHome: 'customerView'
  };
  showSection(map[tab] || 'dashboardView');
}

function showSection(id) {
  document.querySelectorAll('.section-view').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

// ===== ORDER FORM =====
function selectType(type) {
  selectedOrderType = type;
  document.getElementById('typeWhole').classList.toggle('selected', type === 'wholesale');
  document.getElementById('typeRetail').classList.toggle('selected', type === 'retail');
  calcAmount();
}

function selectDate(d) {
  selectedDelivDate = d;
  ['yesterday','today','tomorrow'].forEach(x => {
    document.getElementById('date' + x.charAt(0).toUpperCase() + x.slice(1)).classList.toggle('selected', x === d);
  });
}

function selectPay(p) {
  selectedPayType = p;
  ['Cash','Upi','Udhaar','Advance'].forEach(x => {
    document.getElementById('pay' + x).classList.toggle('selected', x.toLowerCase() === p);
  });
}

function calcAmount() {
  const trays = parseFloat(document.getElementById('orderTrays').value) || 0;
  const rate  = parseFloat(document.getElementById('orderRate').value) || 0;
  const disc  = parseFloat(document.getElementById('discountAmt').value) || 0;
  const trayRate = rate * 30;
  const gross = trays * trayRate;
  const net   = Math.max(0, gross - disc);

  document.getElementById('orderTotal').textContent = '₹' + net.toLocaleString('en-IN');
  document.getElementById('orderSub').textContent = trays + ' Trays × ₹' + trayRate.toFixed(0) + ' per tray';
  document.getElementById('discResult').textContent = disc > 0 ? '−₹' + disc : '−₹0';

  // Stock warning
  const warn = document.getElementById('stockWarning');
  if (trays > availableStock) {
    warn.style.display = 'block';
    document.getElementById('warnAvail').textContent = availableStock;
    document.getElementById('warnAvail2').textContent = availableStock;
  } else { warn.style.display = 'none'; }
}

function searchCustomer(val) {
  const res = document.getElementById('custResults');
  res.style.display = val.length > 1 ? 'block' : 'none';
}

let newCustOpen = false;
function toggleNewCust() {
  newCustOpen = !newCustOpen;
  document.getElementById('newCustFields').style.display = newCustOpen ? 'block' : 'none';
  document.getElementById('custResults').style.display = 'none';
}

function selectCustomer(name, phone, addr) {
  document.getElementById('custSearch').value = name;
  document.getElementById('custResults').style.display = 'none';
  document.getElementById('selectedCust').style.display = 'block';
  document.getElementById('selCustName').textContent = name;
  document.getElementById('selCustInfo').textContent = phone + ' | ' + addr;
  window._selCust = { name, phone, addr };
}

function placeOrder() {
  const trays = parseFloat(document.getElementById('orderTrays').value) || 0;
  const rate  = parseFloat(document.getElementById('orderRate').value) || 0;
  const disc  = parseFloat(document.getElementById('discountAmt').value) || 0;

  if (trays <= 0) { showToast('⚠️ Please enter trays | ट्रे डालें'); return; }

  const cust = window._selCust || { name: document.getElementById('newCustName').value || 'Walk-in Customer', phone: document.getElementById('newCustPhone').value || '—', addr: document.getElementById('newCustAddr').value || '—' };

  const trayRate = rate * 30;
  const total    = Math.max(0, trays * trayRate - disc);
  const recNo    = '#EGG-2025-00' + receiptCounter++;

  currentOrder = { recNo, cust, trays, rate, trayRate, disc, total, delivery: selectedDelivDate, pay: selectedPayType, type: selectedOrderType };

  // Fill receipt
  document.getElementById('recNo').textContent = recNo;
  document.getElementById('recCust').textContent = cust.name;
  document.getElementById('recAddr').textContent = cust.addr;
  document.getElementById('recPhone').textContent = cust.phone;
  document.getElementById('recType').textContent = selectedOrderType === 'wholesale' ? '🏭 Wholesale (थोक)' : '🛒 Retail (पर्चून)';
  document.getElementById('recTrays').textContent = trays + ' Trays (' + (trays * 30) + ' eggs)';
  document.getElementById('recRate').textContent = '₹' + rate;
  document.getElementById('recTrayRate').textContent = '₹' + trayRate.toFixed(0);
  document.getElementById('recTotal').textContent = '₹' + total.toLocaleString('en-IN');
  document.getElementById('recDelivery').textContent = selectedDelivDate.charAt(0).toUpperCase() + selectedDelivDate.slice(1);
  document.getElementById('recPay').textContent = selectedPayType.charAt(0).toUpperCase() + selectedPayType.slice(1);
  document.getElementById('receiptDate').textContent = 'Date: ' + new Date().toLocaleDateString('en-IN');

  if (disc > 0) {
    document.getElementById('recDiscRow').style.display = 'flex';
    document.getElementById('recDisc').textContent = '−₹' + disc;
  } else {
    document.getElementById('recDiscRow').style.display = 'none';
  }

  showSection('receiptView');
  showToast('✅ Order placed! | ऑर्डर हो गया!');
}

function shareWhatsApp() {
  const o = currentOrder;
  const msg = `🥚 *Order Receipt | ऑर्डर रसीद*\n\n*${o.recNo}*\nCustomer: ${o.cust.name}\nTrays: ${o.trays} (${o.trays*30} eggs)\nRate/Egg: ₹${o.rate} | Tray: ₹${o.trayRate.toFixed(0)}\nDelivery: ${o.delivery}\nPayment: ${o.pay}${o.disc>0?'\nDiscount: ₹'+o.disc:''}\n\n*Total: ₹${o.total.toLocaleString('en-IN')}*\n\nThank you! 🙏`;
  window.open('https://wa.me/?text=' + encodeURIComponent(msg));
}

function newOrder() {
  document.getElementById('orderTrays').value = '';
  document.getElementById('discountAmt').value = '';
  document.getElementById('custSearch').value = '';
  document.getElementById('selectedCust').style.display = 'none';
  window._selCust = null;
  showSection('orderView');
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('tab-order').classList.add('active');
}

function markDelivered(btn, trays) {
  const item = btn.closest('.order-item');
  item.classList.remove('reserved', 'pending-pay');
  item.classList.add('delivered');
  btn.remove();
  const reservedTag = item.querySelector('.tag.reserved-tag');
  if (reservedTag) { reservedTag.className = 'tag delivered-tag'; reservedTag.textContent = '✅ Delivered'; }
  availableStock = Math.max(0, availableStock - trays);
  document.getElementById('stockAvailable').textContent = availableStock;
  showToast('✅ Delivered! Stock updated | डिलीवर हो गई');
}

// ===== BROKEN EGGS =====
function addBrokenEggs() {
  const add = parseInt(document.getElementById('brokenInput').value) || 0;
  if (add <= 0) return;
  brokenEggsCount += add;
  document.getElementById('brokenInput').value = '';

  const newTrays = Math.floor(brokenEggsCount / 30);
  if (newTrays > brokenTrays) {
    const diff = newTrays - brokenTrays;
    brokenTrays = newTrays;
    availableStock = Math.max(0, availableStock - diff);
    document.getElementById('stockAvailable').textContent = availableStock;
    showToast('❌ ' + diff + ' broken tray(s) counted!');
  }

  const rem = brokenEggsCount % 30;
  document.getElementById('brokenCount').textContent = rem;
  document.getElementById('brokenBar').style.width = (rem / 30 * 100) + '%';
  document.getElementById('brokenTraysCount').textContent = brokenTrays + ' trays broken | ' + brokenTrays + ' ट्रे टूटी';
  document.getElementById('stockBroken').textContent = '−' + brokenTrays;
}

// ===== RATE UPDATE =====
function calcFinalRate() {
  const p = parseFloat(document.getElementById('purchaseRate').value) || 0;
  const t = parseFloat(document.getElementById('transportCost').value) || 0;
  const m = parseFloat(document.getElementById('marginAmt').value) || 0;
  const d = parseFloat(document.getElementById('deliveryCharge').value) || 0;
  const final = p + t + m + d;
  const tray  = final * 30;
  document.getElementById('finalEggRate').textContent = '₹' + final.toFixed(2);
  document.getElementById('finalTrayRate').textContent = '₹' + tray.toFixed(0);
  document.getElementById('waPreview').textContent =
    `🥚 Aaj ka Egg Rate 🥚\n1 Anda = ₹${final.toFixed(2)}\n1 Tray (30 Ande) = ₹${tray.toFixed(0)}\n\nOrder ke liye sampark karein 📞`;
}

function updateRate() {
  const rate = document.getElementById('finalEggRate').textContent;
  const tray = document.getElementById('finalTrayRate').textContent;
  document.getElementById('dashRate').textContent = rate;
  document.getElementById('dashTrayRate').textContent = '1 Tray = ' + tray;
  showToast('✅ Rate updated! | रेट अपडेट हो गया!');
}

function copyWaMessage() {
  const msg = document.getElementById('waPreview').textContent;
  navigator.clipboard.writeText(msg).then(() => showToast('✅ Copied! Paste in WhatsApp | कॉपी हो गया'));
}

function addStock() {
  const n = parseInt(document.getElementById('newStock').value) || 0;
  if (n <= 0) { showToast('⚠️ Enter number of trays | ट्रे की संख्या डालें'); return; }
  availableStock += n;
  document.getElementById('stockAvailable').textContent = availableStock;
  document.getElementById('stockNew').textContent = '+' + n;
  document.getElementById('newStock').value = '';
  showToast('✅ ' + n + ' trays added | ट्रे जोड़ी गईं');
}

// ===== REPORTS =====
function filterOrders(type, el) {
  document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
  el.classList.add('active');
  showToast('Filter: ' + type);
}

// ===== CUSTOMER =====
function custCalc() {
  const t = parseFloat(document.getElementById('custTrays').value) || 0;
  document.getElementById('custTotal').textContent = '₹' + (t * 195).toLocaleString('en-IN');
}

function custDate(d) {
  custSelectedDate = d;
  document.getElementById('custToday').classList.toggle('selected', d === 'today');
  document.getElementById('custTomorrow').classList.toggle('selected', d === 'tomorrow');
}

function custPlaceOrder() {
  const t = parseFloat(document.getElementById('custTrays').value) || 0;
  if (t <= 0) { showToast('⚠️ Enter trays | ट्रे डालें'); return; }
  showToast('✅ Order placed! Admin will confirm | ऑर्डर हो गया!');
}

// ===== TOAST =====
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 2800);
}
</script>
</body>
</html>
