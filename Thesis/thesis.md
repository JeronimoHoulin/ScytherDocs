<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Scyther Thesis</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap');

  :root {
    --bg: #0a0c10;
    --surface: #111318;
    --surface2: #181c24;
    --border: #1e2430;
    --accent: #00e5a0;
    --accent2: #0090ff;
    --text: #e2e8f0;
    --muted: #64748b;
    --soft: #94a3b8;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    padding: 48px 24px;
  }

  .container { max-width: 760px; margin: 0 auto; }

  /* Header */
  .hero {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 48px;
  }
  .hero-icon {
    width: 48px; height: 48px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    flex-shrink: 0;
  }
  h1 {
    font-size: 28px;
    font-weight: 700;
    background: linear-gradient(90deg, #fff 0%, var(--accent) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    letter-spacing: -0.5px;
  }
  .subtitle { color: var(--muted); font-size: 13px; margin-top: 2px; }

  /* Sections */
  section { margin-bottom: 48px; }

  h2 {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
    padding-bottom: 10px;
    border-bottom: 1px solid var(--border);
  }

  h3 {
    font-size: 14px;
    font-weight: 600;
    color: #fff;
    margin: 24px 0 8px;
  }

  p { color: var(--soft); margin-bottom: 12px; }

  /* Objectives cards */
  .obj-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  @media (max-width: 560px) { .obj-grid { grid-template-columns: 1fr; } }

  .obj-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    position: relative;
    overflow: hidden;
  }
  .obj-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
  }
  .obj-card.alpha::before { background: linear-gradient(90deg, var(--accent), transparent); }
  .obj-card.trust::before { background: linear-gradient(90deg, var(--accent2), transparent); }

  .obj-num {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .obj-card.alpha .obj-num { color: var(--accent); }
  .obj-card.trust .obj-num { color: var(--accent2); }

  .obj-title {
    font-size: 16px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 14px;
  }

  .obj-items { list-style: none; }
  .obj-items li {
    color: var(--soft);
    font-size: 13.5px;
    padding: 5px 0;
    display: flex;
    gap: 8px;
    align-items: flex-start;
  }
  .obj-items li::before {
    content: '—';
    flex-shrink: 0;
    margin-top: 1px;
  }
  .obj-card.alpha .obj-items li::before { color: var(--accent); }
  .obj-card.trust .obj-items li::before { color: var(--accent2); }

  /* Architecture */
  .arch-diagram {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 24px;
  }

  .flow {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  .flow-node {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 16px;
    text-align: center;
    min-width: 130px;
  }
  .flow-node .node-label {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 3px;
  }
  .flow-node .node-sub { font-size: 12px; color: var(--muted); }
  .flow-node.vault .node-label { color: var(--accent); }
  .flow-node.roles .node-label { color: #a78bfa; }
  .flow-node.operator .node-label { color: var(--accent2); }

  .flow-arrow { color: var(--muted); font-size: 18px; flex-shrink: 0; }

  .arch-note {
    text-align: center;
    font-size: 12px;
    color: var(--muted);
    margin-top: 16px;
  }
  .arch-note a { color: #a78bfa; text-decoration: none; }
  .arch-note a:hover { text-decoration: underline; }

  /* Component cards */
  .component-list { display: flex; flex-direction: column; gap: 12px; }
  .comp-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px 20px;
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }
  .comp-badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    font-weight: 500;
    padding: 4px 8px;
    border-radius: 6px;
    white-space: nowrap;
    flex-shrink: 0;
    margin-top: 2px;
  }
  .badge-a { background: rgba(0,229,160,0.1); color: var(--accent); border: 1px solid rgba(0,229,160,0.2); }
  .badge-roles { background: rgba(167,139,250,0.1); color: #a78bfa; border: 1px solid rgba(167,139,250,0.2); }
  .badge-b { background: rgba(0,144,255,0.1); color: var(--accent2); border: 1px solid rgba(0,144,255,0.2); }
  .badge-tom { background: rgba(251,191,36,0.1); color: #fbbf24; border: 1px solid rgba(251,191,36,0.2); }

  .comp-content .comp-name { font-weight: 600; color: #fff; margin-bottom: 4px; font-size: 14px; }
  .comp-content p { font-size: 13.5px; margin: 0; color: var(--soft); }
  .comp-content a { color: #a78bfa; text-decoration: none; }
  .comp-content a:hover { text-decoration: underline; }

  /* Trust table */
  .trust-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 14px;
    margin-bottom: 16px;
  }
  .trust-table thead tr {
    border-bottom: 1px solid var(--border);
  }
  .trust-table th {
    text-align: left;
    padding: 10px 14px;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--muted);
  }
  .trust-table td {
    padding: 12px 14px;
    color: var(--soft);
    border-bottom: 1px solid rgba(30,36,48,0.6);
    vertical-align: top;
  }
  .trust-table tr:last-child td { border-bottom: none; }
  .trust-table td:first-child {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    font-weight: 600;
    width: 32px;
  }
  .trust-table tr { background: var(--surface); }
  .trust-table tr:nth-child(even) { background: var(--surface2); }

  .trust-note {
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent2);
    border-radius: 0 8px 8px 0;
    padding: 14px 16px;
    font-size: 13.5px;
    color: var(--soft);
  }

  /* Farms */
  .farms-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  @media (max-width: 560px) { .farms-grid { grid-template-columns: 1fr; } }

  .farm-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    position: relative;
    overflow: hidden;
  }
  .farm-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 80px;
    pointer-events: none;
    border-radius: 0 0 12px 12px;
  }
  .farm-card.usd::after { background: radial-gradient(ellipse at bottom, rgba(0,229,160,0.06) 0%, transparent 70%); }
  .farm-card.eth::after { background: radial-gradient(ellipse at bottom, rgba(0,144,255,0.06) 0%, transparent 70%); }

  .farm-token {
    font-family: 'JetBrains Mono', monospace;
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 14px;
  }
  .farm-card.usd .farm-token { color: var(--accent); }
  .farm-card.eth .farm-token { color: var(--accent2); }

  .farm-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 7px 0;
    border-bottom: 1px solid var(--border);
    font-size: 13px;
  }
  .farm-row:last-of-type { border-bottom: none; }
  .farm-key { color: var(--muted); font-size: 12px; text-transform: uppercase; letter-spacing: 0.5px; }
  .farm-val { color: var(--text); font-weight: 500; }

  .farms-footnote {
    font-size: 12.5px;
    color: var(--muted);
    margin-top: 14px;
    font-style: italic;
  }

  hr { display: none; }

  tag { display: inline-block; background: rgba(167,139,250,0.1); color: #a78bfa; border: 1px solid rgba(167,139,250,0.2); font-size: 11px; padding: 2px 7px; border-radius: 4px; font-family: 'JetBrains Mono', monospace; }
</style>
</head>
<body>
<div class="container">

  <div class="hero">
    <div class="hero-icon">⚔️</div>
    <div>
      <h1>Scyther Thesis</h1>
      <div class="subtitle">DeFi Yield Strategy — Architecture & Trust Model</div>
    </div>
  </div>

  <!-- Objectives -->
  <section>
    <h2>Objectives</h2>
    <div class="obj-grid">
      <div class="obj-card alpha">
        <div class="obj-num">01</div>
        <div class="obj-title">Generate Alpha</div>
        <ul class="obj-items">
          <li>Chase yield in DeFi above benchmark (Aave & Lido APYs)</li>
          <li>Farm points</li>
          <li>Auto-compound returns back into the same vault</li>
        </ul>
      </div>
      <div class="obj-card trust">
        <div class="obj-num">02</div>
        <div class="obj-title">Minimize Trust</div>
        <ul class="obj-items">
          <li>Anyone can withdraw before portfolio changes execute</li>
          <li>Deposits & withdrawals settle weekly</li>
          <li>New permissions execute with a one-month delay + TG notice</li>
          <li>Users get 4 windows to propose changes or exit</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- Architecture -->
  <section>
    <h2>Architecture</h2>
    <div class="arch-diagram">
      <div class="flow">
        <div class="flow-node vault">
          <div class="node-label">Safe A</div>
          <div class="node-sub">The Vault</div>
        </div>
        <div class="flow-arrow">→</div>
        <div class="flow-node roles">
          <div class="node-label">Roles Modifier</div>
          <div class="node-sub">Enforces rules</div>
        </div>
        <div class="flow-arrow">→</div>
        <div class="flow-node operator">
          <div class="node-label">Safe B</div>
          <div class="node-sub">The Operator</div>
        </div>
      </div>
      <p class="arch-note">Permission boundary enforced by <a href="https://docs.roles.gnosisguild.org/" target="_blank">Zodiac Roles Modifier</a></p>
    </div>

    <div class="component-list">
      <div class="comp-card">
        <span class="comp-badge badge-a">Safe A</span>
        <div class="comp-content">
          <div class="comp-name">The Vault</div>
          <p>Holds 100% of capital. Any transaction not explicitly pre-approved by the Roles Modifier will revert — the operator cannot execute outside the defined scope.</p>
        </div>
      </div>
      <div class="comp-card">
        <span class="comp-badge badge-roles">Roles</span>
        <div class="comp-content">
          <div class="comp-name">Roles Modifier</div>
          <p>A contract deployed by Safe A that grants Safe B a narrowly scoped set of permissions. Nothing outside those permissions can happen — not even if Safe B is compromised. See the <a href="https://docs.roles.gnosisguild.org/" target="_blank">Zodiac Roles Modifier docs</a>.</p>
        </div>
      </div>
      <div class="comp-card">
        <span class="comp-badge badge-b">Safe B</span>
        <div class="comp-content">
          <div class="comp-name">The Operator</div>
          <p>Executes the strategy, rebalances, and disassembles as needed. Can only perform pre-approved actions.</p>
        </div>
      </div>
      <div class="comp-card">
        <span class="comp-badge badge-tom">Tom</span>
        <div class="comp-content">
          <div class="comp-name">The Agent</div>
          <p>Holds a <a href="https://help.safe.global/en/articles/235770-proposers" target="_blank">Proposer</a> role within Safe B — can queue transactions but cannot execute unilaterally. AI speeds up operations without introducing unilateral control.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Trust Model -->
  <section>
    <h2>Trust Model</h2>
    <p style="margin-bottom:16px;">The Operator requires the Vault's approval before interacting with any new protocol, pool, or contract. The following conditions govern how new permissions are granted:</p>
    <table class="trust-table">
      <thead>
        <tr>
          <th>#</th>
          <th>Condition</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>New permissions are publicly announced in the Telegram channel <strong style="color:#e2e8f0;">"Permission Proposals"</strong></td>
        </tr>
        <tr>
          <td>2</td>
          <td>A <strong style="color:#e2e8f0;">30-day waiting period</strong> must pass between a proposal and its execution</td>
        </tr>
        <tr>
          <td>3</td>
          <td>The Vault settles every <strong style="color:#e2e8f0;">7 days</strong>, giving users <strong style="color:#e2e8f0;">4 withdrawal windows</strong> to exit before any new permission takes effect</td>
        </tr>
      </tbody>
    </table>
    <div class="trust-note">No new capital exposure can be introduced without public notice and a meaningful window for users to withdraw if they disagree.</div>
  </section>

  <!-- Farms -->
  <section>
    <h2>The Farms</h2>
    <p style="margin-bottom:16px;">Scyther will launch with USD &amp; ETH denominated farms.</p>
    <div class="farms-grid">
      <div class="farm-card usd">
        <div class="farm-token">scyUSD</div>
        <div class="farm-row"><span class="farm-key">Underlying</span><span class="farm-val">USDC</span></div>
        <div class="farm-row"><span class="farm-key">Entry chain</span><span class="farm-val">Ethereum mainnet</span></div>
        <div class="farm-row"><span class="farm-key">Exit chain</span><span class="farm-val">Ethereum mainnet</span></div>
      </div>
      <div class="farm-card eth">
        <div class="farm-token">scyETH</div>
        <div class="farm-row"><span class="farm-key">Underlying</span><span class="farm-val">WETH</span></div>
        <div class="farm-row"><span class="farm-key">Entry chain</span><span class="farm-val">Ethereum mainnet</span></div>
        <div class="farm-row"><span class="farm-key">Exit chain</span><span class="farm-val">Ethereum mainnet</span></div>
      </div>
    </div>
    <p class="farms-footnote">* Vaults can move assets cross-chain, but always under the same address custody — assets never leave the vault.</p>
  </section>

</div>
</body>
</html>
