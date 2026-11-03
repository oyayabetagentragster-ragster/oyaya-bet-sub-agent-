<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Oyaya Bet - Agent Portal</title>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
  <style>
    :root {
      --primary: #0f172a;
      --primary-light: #1e293b;
      --accent: #2563eb;
      --bg-body: #f1f5f9;
      --card-bg: #ffffff;
      --text-main: #0f172a;
      --text-muted: #64748b;
      --border: #e2e8f0;
      --success: #16a34a;
      --warning: #d97706;
      --danger: #dc2626;
      --radius: 12px;
      --shadow: 0 4px 6px -1px rgb(0 0 0 / 0.05);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      background-color: var(--bg-body);
      color: var(--text-main);
      padding-bottom: 70px;
    }

    /* Mobile First Navigation Bar */
    .navbar {
      background-color: var(--primary);
      color: #fff;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 10px rgba(0,0,0,0.15);
    }

    .nav-top {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 12px 16px;
    }

    .brand-title {
      font-size: 16px;
      font-weight: 700;
      letter-spacing: 0.5px;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .header-actions {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .balance-chip {
      background: rgba(255, 255, 255, 0.1);
      padding: 6px 12px;
      border-radius: 20px;
      font-size: 13px;
      font-weight: 700;
      border: 1px solid rgba(255, 255, 255, 0.15);
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .status-badge {
      background: #22c55e;
      color: #fff;
      padding: 4px 8px;
      border-radius: 12px;
      font-size: 11px;
      font-weight: 700;
    }

    /* Horizontally Scrollable Menu Tabs */
    .menu-bar {
      display: flex;
      overflow-x: auto;
      background: var(--primary-light);
      padding: 0 8px;
      scrollbar-width: none;
    }

    .menu-bar::-webkit-scrollbar { display: none; }

    .nav-tab {
      padding: 12px 14px;
      color: #94a3b8;
      font-size: 13px;
      font-weight: 600;
      white-space: nowrap;
      border-bottom: 3px solid transparent;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .nav-tab.active {
      color: #fff;
      border-bottom-color: var(--accent);
    }

    /* Main Container */
    .container {
      max-width: 500px;
      margin: 0 auto;
      padding: 12px;
    }

    .tab-content { display: none; }
    .tab-content.active { display: block; }

    /* Modern Card Layout */
    .card {
      background: var(--card-bg);
      border-radius: var(--radius);
      border: 1px solid var(--border);
      padding: 16px;
      margin-bottom: 12px;
      box-shadow: var(--shadow);
    }

    .card-title {
      font-size: 15px;
      font-weight: 700;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    /* Inputs & Selects */
    .form-group { margin-bottom: 12px; }
    .form-label {
      display: block;
      font-size: 12px;
      font-weight: 600;
      color: var(--text-muted);
      margin-bottom: 4px;
    }

    .form-control {
      width: 100%;
      padding: 12px;
      border: 1px solid var(--border);
      border-radius: 8px;
      font-size: 14px;
      background: #f8fafc;
      transition: border 0.2s;
    }

    .form-control:focus {
      outline: none;
      border-color: var(--accent);
      background: #fff;
    }

    /* Buttons */
    .btn {
      width: 100%;
      padding: 12px;
      border-radius: 8px;
      font-weight: 600;
      font-size: 14px;
      border: none;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .btn-primary { background: var(--accent); color: white; }
    .btn-secondary { background: #e2e8f0; color: var(--text-main); }
    .btn-sm { padding: 6px 12px; font-size: 12px; width: auto; }

    /* Compact Stat Cards */
    .stat-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 8px;
      margin-bottom: 12px;
    }

    .stat-box {
      background: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 10px;
      text-align: center;
    }

    .stat-box .val {
      font-size: 16px;
      font-weight: 800;
      margin-top: 2px;
    }

    .stat-box .lbl {
      font-size: 11px;
      color: var(--text-muted);
    }

    /* Custom Mobile Cards for Table Data */
    .bank-card {
      background: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 12px;
      margin-bottom: 10px;
    }

    .bank-card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 6px;
    }

    .bank-name { font-weight: 700; font-size: 14px; }
    .bank-num { font-size: 13px; color: var(--text-muted); margin-bottom: 4px; }

    /* Modals */
    .modal-overlay {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.6);
      z-index: 200;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-overlay.active { display: flex; }

    .modal-box {
      background: white;
      border-radius: var(--radius);
      width: 100%;
      max-width: 400px;
      padding: 16px;
    }
  </style>
</head>
<body>

  <!-- Top App Navigation -->
  <header class="navbar">
    <div class="nav-top">
      <div class="brand-title">
        <i class="fa-solid fa-shield-halved" style="color: #60a5fa;"></i>
        <span>Oyaya Bet</span>
      </div>
      <div class="header-actions">
        <div class="balance-chip">
          <i class="fa-solid fa-wallet"></i>
          <span>ETB 0.00</span>
        </div>
        <span class="status-badge">Active</span>
      </div>
    </div>
    
    <!-- Mobile Horizontal Tabs -->
    <div class="menu-bar">
      <div class="nav-tab active" data-tab="payment-requests"><i class="fa-solid fa-receipt"></i> Requests</div>
      <div class="nav-tab" data-tab="banks"><i class="fa-solid fa-building-columns"></i> Banks</div>
      <div class="nav-tab" data-tab="sms"><i class="fa-solid fa-message"></i> SMS</div>
      <div class="nav-tab" data-tab="reports"><i class="fa-solid fa-chart-pie"></i> Reports</div>
      <div class="nav-tab" data-tab="account"><i class="fa-solid fa-user"></i> Account</div>
    </div>
  </header>

  <!-- Content Sections -->
  <main class="container">

    <!-- REQUESTS TAB -->
    <section id="payment-requests" class="tab-content active">
      <div class="card">
        <div class="card-title">Filter Transactions</div>
        <div class="form-group">
          <input type="text" class="form-control" placeholder="Player or Phone number">
        </div>
        <div class="form-group" style="display: flex; gap: 8px;">
          <select class="form-control">
            <option>All Types</option>
            <option>Deposit</option>
            <option>Withdrawal</option>
          </select>
          <select class="form-control">
            <option>All Statuses</option>
            <option>Pending</option>
            <option>Successful</option>
            <option>Failed</option>
          </select>
        </div>
        <button class="btn btn-primary"><i class="fa-solid fa-magnifying-glass"></i> Search</button>
      </div>

      <div class="stat-row">
        <div class="stat-box">
          <div class="lbl">Successful</div>
          <div class="val" style="color: var(--success);">0</div>
          <div class="lbl"># 0.00</div>
        </div>
        <div class="stat-box">
          <div class="lbl">Pending</div>
          <div class="val" style="color: var(--warning);">0</div>
          <div class="lbl"># 0.00</div>
        </div>
        <div class="stat-box">
          <div class="lbl">Failed</div>
          <div class="val" style="color: var(--danger);">0</div>
          <div class="lbl"># 0.00</div>
        </div>
      </div>

      <div class="card" style="text-align: center; color: var(--text-muted); padding: 30px;">
        <i class="fa-solid fa-folder-open" style="font-size: 32px; margin-bottom: 8px;"></i>
        <p>No transactions found</p>
      </div>
    </section>

    <!-- BANKS & WALLETS TAB -->
    <section id="banks" class="tab-content">
      <div class="card">
        <div class="card-title">
          <span>Banks & Wallets</span>
          <button class="btn btn-primary btn-sm" id="openAddBankModal"><i class="fa-solid fa-plus"></i> Attach Bank</button>
        </div>
        <div id="bankListContainer">
          <!-- Dynamically filled -->
        </div>
      </div>
    </section>

    <!-- SMS VERIFICATION TAB -->
    <section id="sms" class="tab-content">
      <div class="card">
        <div class="card-title">SMS Verification</div>
        <div class="form-group">
          <textarea class="form-control" rows="4" placeholder="Paste bank SMS here..."></textarea>
        </div>
        <button class="btn btn-primary">Verify SMS</button>
      </div>
    </section>

    <!-- REPORTS TAB -->
    <section id="reports" class="tab-content">
      <div class="card">
        <div class="card-title">Report Summary</div>
        <div class="form-group">
          <select class="form-control">
            <option>Today</option>
            <option>This Week</option>
            <option>This Month</option>
          </select>
        </div>
        <div class="stat-row">
          <div class="stat-box">
            <div class="lbl">Deposits</div>
            <div class="val">0</div>
          </div>
          <div class="stat-box">
            <div class="lbl">Withdrawals</div>
            <div class="val">0</div>
          </div>
          <div class="stat-box">
            <div class="lbl">Commission</div>
            <div class="val"># 0.00</div>
          </div>
        </div>
      </div>
    </section>

    <!-- ACCOUNT TAB -->
    <section id="account" class="tab-content">
      <div class="card">
        <div class="card-title">Attendance</div>
        <div style="background: #f0fdf4; border: 1px solid #bbf7d0; padding: 10px; border-radius: 8px; margin-bottom: 10px;">
          <span style="font-size: 11px; color: #166534; font-weight: 700;">STATUS</span>
          <div style="font-weight: 700; color: #15803d;">Clocked in</div>
        </div>
        <button class="btn btn-secondary btn-sm"><i class="fa-solid fa-clock"></i> Clock Out</button>
      </div>

      <div class="card">
        <div class="card-title">Wallet Balance</div>
        <div style="font-size: 24px; font-weight: 800; color: var(--primary);">0.00 ETB</div>
      </div>
    </section>

  </main>

  <!-- Add/Edit Bank Modal -->
  <div class="modal-overlay" id="bankModal">
    <div class="modal-box">
      <div class="card-title" id="modalTitle">Attach Bank</div>
      <form id="bankForm">
        <input type="hidden" id="editIdx" value="-1">
        <div class="form-group">
          <label class="form-label">Method</label>
          <select class="form-control" id="mMethod">
            <option>telebirr</option>
            <option>Commercial Bank of Ethiopia</option>
            <option>Bank of Abyssinia</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Account Number</label>
          <input type="text" class="form-control" id="mAccNum" placeholder="Account Number" required>
        </div>
        <div class="form-group">
          <label class="form-label">Account Name</label>
          <input type="text" class="form-control" id="mAccName" placeholder="Account Name" required>
        </div>
        <div class="form-group">
          <label class="form-label">Status</label>
          <select class="form-control" id="mStatus">
            <option value="Active">Active</option>
            <option value="Inactive">Inactive</option>
          </select>
        </div>
        <div style="display: flex; gap: 8px; margin-top: 16px;">
          <button type="button" class="btn btn-secondary" id="closeModal">Cancel</button>
          <button type="submit" class="btn btn-primary">Save</button>
        </div>
      </form>
    </div>
  </div>

  <script>
    // Tab Navigation
    const tabs = document.querySelectorAll('.nav-tab');
    const contents = document.querySelectorAll('.tab-content');

    tabs.forEach(tab => {
      tab.addEventListener('click', () => {
        tabs.forEach(t => t.classList.remove('active'));
        contents.forEach(c => c.classList.remove('active'));
        tab.classList.add('active');
        document.getElementById(tab.dataset.tab).classList.add('active');
      });
    });

    // Dynamic Banks State
    let banks = [];

    const bankContainer = document.getElementById('bankListContainer');
    const bankModal = document.getElementById('bankModal');
    const openAddModalBtn = document.getElementById('openAddBankModal');
    const closeModalBtn = document.getElementById('closeModal');
    const bankForm = document.getElementById('bankForm');

    function renderBanks() {
      bankContainer.innerHTML = '';
      if (banks.length === 0) {
        bankContainer.innerHTML = `<p style="text-align:center; color: var(--text-muted); padding: 16px;">No banks added yet.</p>`;
        return;
      }
      banks.forEach((b, i) => {
        const div = document.createElement('div');
        div.className = 'bank-card';
        div.innerHTML = `
          <div class="bank-card-header">
            <span class="bank-name">${b.method}</span>
            <span class="status-badge" style="background:${b.status === 'Active' ? '#22c55e' : '#ef4444'}">${b.status}</span>
          </div>
          <div class="bank-num">${b.accNum} - ${b.accName}</div>
          <div style="display:flex; gap:6px; margin-top:8px;">
            <button class="btn btn-secondary btn-sm" onclick="editBank(${i})">Edit</button>
            <button class="btn btn-secondary btn-sm" onclick="deleteBank(${i})">Delete</button>
          </div>
        `;
        bankContainer.appendChild(div);
      });
    }

    openAddModalBtn.addEventListener('click', () => {
      document.getElementById('editIdx').value = "-1";
      document.getElementById('modalTitle').innerText = "Attach Bank";
      bankForm.reset();
      bankModal.classList.add('active');
    });

    closeModalBtn.addEventListener('click', () => bankModal.classList.remove('active'));

    bankForm.addEventListener('submit', (e) => {
      e.preventDefault();
      const idx = parseInt(document.getElementById('editIdx').value);
      const data = {
        method: document.getElementById('mMethod').value,
        accNum: document.getElementById('mAccNum').value,
        accName: document.getElementById('mAccName').value,
        status: document.getElementById('mStatus').value
      };
      if (idx >= 0) { banks[idx] = data; } else { banks.push(data); }
      renderBanks();
      bankModal.classList.remove('active');
    });

    window.editBank = function(i) {
      const b = banks[i];
      document.getElementById('mMethod').value = b.method;
      document.getElementById('mAccNum').value = b.accNum;
      document.getElementById('mAccName').value = b.accName;
      document.getElementById('mStatus').value = b.status;
      document.getElementById('editIdx').value = i;
      document.getElementById('modalTitle').innerText = "Edit Bank";
      bankModal.classList.add('active');
    };

    window.deleteBank = function(i) {
      if (confirm('Delete this account?')) {
        banks.splice(i, 1);
        renderBanks();
      }
    };

    renderBanks();
  </script>
</body>
</html>
