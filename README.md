<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Understanding Your ID Card</title>

<style>
  :root{
    --bg:#0d1117;
    --card:#1c1f26;
    --text:#e6edf3;
    --muted:#8b949e;
    --brand:#2f81f7;      /* HPHP-ish blue */
    --brand2:#ff9800;     /* hover */
    --shadow: 0 14px 35px rgba(0,0,0,.4);
    --radius: 14px;
  }

  *{ box-sizing:border-box; }

  body{
    margin:0;
    font-family: system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
    background:var(--bg);
    color:var(--text);
  }

  header{
    padding:28px 14px 10px;
    text-align:center;
  }
  header h1{
    margin:0 0 6px;
    font-size: clamp(22px, 2.6vw, 34px);
  }
  header p{
    margin:0;
    color:var(--muted);
    font-size: 15px;
  }

  .page{
    max-width:1200px;
    margin: 0 auto;
    padding: 18px 14px 60px;
  }

  .plan-section{
    background: rgba(28,31,38,.6);
    border: 1px solid rgba(255,255,255,.1);
    border-radius: var(--radius);
    padding: 18px;
    margin-top: 18px;
  }

  .plan-head{
    display:flex;
    align-items:flex-start;
    justify-content:space-between;
    gap:12px;
    flex-wrap:wrap;
    margin-bottom: 14px;
  }
  .plan-head h2{
    margin:0;
    font-size: 20px;
  }
  .plan-head .sub{
    margin:4px 0 0;
    color:var(--muted);
    font-size: 14px;
    max-width: 80ch;
  }

  .toggle{
    display:flex;
    gap:8px;
    background: rgba(47,129,247,.15);
    padding:6px;
    border-radius: 999px;
    border: 1px solid rgba(47,129,247,.25);
  }
  .toggle button{
    border:0;
    background: transparent;
    padding:8px 12px;
    border-radius: 999px;
    cursor:pointer;
    font-weight: 700;
    color: var(--brand);
    transition: .15s ease;
  }
  .toggle button.active{
    background: var(--brand);
    color: white;
    box-shadow: 0 8px 18px rgba(47,129,247,.35);
  }

  .layout{
    display:grid;
    grid-template-columns: minmax(320px, 1.35fr) minmax(280px, .85fr);
    gap: 18px;
    align-items:start;
  }

  @media (max-width: 980px){
    .layout{ grid-template-columns: 1fr; }
  }

  .image-wrap{
    position:relative;
    background: var(--card);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    overflow: visible; /* allow pins outside */
    border: 1px solid rgba(255,255,255,.1);
    padding: 10px;     /* breathing room for outside pins */
  }

  .image-wrap .img-frame{
    position: relative;
    border-radius: calc(var(--radius) - 4px);
    overflow: hidden;
  }

  .image-wrap img{
    width:100%;
    height:auto;
    display:block;
  }

  /* ===== CALLOUT PINS (circle outside + leader line to target) ===== */
  .pin{
    position:absolute;
    left: var(--px);
    top: var(--py);
    transform: translate(-50%, -50%);
    z-index: 5;
  }

  .pin button{
    width: 24px;
    height: 24px;
    border-radius: 999px;
    border: 2px solid rgba(255,255,255,.92);
    background: var(--brand);
    color:#fff;
    font-weight: 800;
    font-size: 12px;
    cursor:pointer;
    box-shadow: 0 6px 16px rgba(47,129,247,.4);
    display:flex;
    align-items:center;
    justify-content:center;
    padding:0;
    line-height: 1;
    transition: .18s ease;
  }

  .pin button:hover{
    background: var(--brand2);
    transform: scale(1.06);
  }

  .pin::after{
    content:"";
    position:absolute;
    left: 50%;
    top: 50%;
    width: var(--len, 60px);
    height: 2px;
    background: rgba(47,129,247,.85);
    transform-origin: 0 50%;
    transform: rotate(var(--ang, 0deg));
    border-radius: 2px;
  }

  /* Info panel */
  .panel{
    background: var(--card);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    border: 1px solid rgba(255,255,255,.1);
    padding: 18px;
    position: sticky;
    top: 14px;
  }
  @media (max-width: 980px){
    .panel{ position: static; }
  }

  .panel h3{
    margin:0 0 8px;
    font-size: 18px;
  }
  .panel p{
    margin: 0 0 10px;
    color: var(--muted);
    line-height: 1.45;
  }
  .tip{
    margin-top: 12px;
    padding: 12px;
    border-left: 4px solid var(--brand);
    background: rgba(47,129,247,.12);
    border-radius: 10px;
  }
  .tip strong{ color: var(--text); }
  .mini{
    font-size: 12.5px;
    color: var(--muted);
    margin-top: 10px;
  }

  .divider{
    margin-top: 18px;
    height: 1px;
    background: rgba(255,255,255,.1);
  }
</style>
</head>

<body>

<header>
  <h1>Understanding Your ID Card</h1>
  <p>Use this interactive guide to better understand the information on your ID Card, what numbers and information healthcare providers need, and where to call for help.</p>
</header>

<div class="page">

  <!-- =========================
       HPI SECTION
       ========================= -->
  <section class="plan-section" id="hpi-section">
    <div class="plan-head">
      <div>
        <h2>HPI Member ID Card (Example)</h2>
        <p class="sub">Front and back example for members whose TPA is Health Plans, Inc. (HPI).  If you ever experience issues with a heatlhcare provider verifying any of this information, pleaes ask them to call HPHP Concierge directly at 806-510-HPHP (4747).</p>
      </div>

      <div class="toggle" aria-label="Toggle front/back (HPI)">
        <button type="button" class="active" id="hpiFrontBtn" onclick="showSide('hpi','front')">Front</button>
        <button type="button" id="hpiBackBtn" onclick="showSide('hpi','back')">Back</button>
      </div>
    </div>

    <div class="layout">

      <!-- HPI FRONT -->
      <div class="image-wrap" id="hpiFrontWrap">
        <div class="img-frame">
          <img
            src="https://hphealthplan.com/wp-content/uploads/2026/02/hpi-card-front-updated.jpg"
            alt="HPI ID Card Front"
          />
        </div>

        <!-- Pins (outside) + targets (inside) -->
        <div class="pin" style="--px: 2%; --py: 22%;" data-tx="24" data-ty="24">
          <button type="button" onclick="showInfo('hpi',1)">1</button>
        </div>

        <div class="pin" style="--px: 98%; --py: 22%;" data-tx="74" data-ty="24">
          <button type="button" onclick="showInfo('hpi',2)">2</button>
        </div>

        <div class="pin" style="--px: 98%; --py: 70%;" data-tx="74" data-ty="66">
          <button type="button" onclick="showInfo('hpi',3)">3</button>
        </div>

        <div class="pin" style="--px: 2%; --py: 70%;" data-tx="28" data-ty="66">
          <button type="button" onclick="showInfo('hpi',4)">4</button>
        </div>
      </div>

      <!-- HPI BACK -->
      <div class="image-wrap" id="hpiBackWrap" style="display:none;">
        <div class="img-frame">
          <img
            src="https://hphealthplan.com/wp-content/uploads/2026/02/HPI-Card-back-png.png"
            alt="HPI ID Card Back"
          />
        </div>

        <div class="pin" style="--px: 2%; --py: 30%;" data-tx="26" data-ty="34">
          <button type="button" onclick="showInfo('hpi',5)">5</button>
        </div>

        <div class="pin" style="--px: 2%; --py: 84%;" data-tx="24" data-ty="80">
          <button type="button" onclick="showInfo('hpi',6)">6</button>
        </div>

        <div class="pin" style="--px: 98%; --py: 84%;" data-tx="62" data-ty="80">
          <button type="button" onclick="showInfo('hpi',7)">7</button>
        </div>
      </div>

      <!-- HPI PANEL -->
      <aside class="panel" id="hpiPanel">
        <h3>Click a number on the card</h3>
        <p>We’ll explain what that section is for, plus tips to avoid common issues (billing delays, eligibility confusion, etc.).</p>
        <div class="tip">
          <strong>Quick tip:</strong> If a provider’s office is confused, have them call the HPHP Concierge number on the back of the card - 806-510-HPHP(4747).
        </div>
        <div class="mini">This page is an educational example and does not replace real-time eligibility/benefit verification.</div>
      </aside>

    </div>
  </section>

  <!-- =========================
       LUCENT SECTION
       ========================= -->
  <section class="plan-section" id="lucent-section">
    <div class="plan-head">
      <div>
        <h2>Lucent Health Member ID Card (Example)</h2>
        <p class="sub">Front and back example for members whose TPA is Lucent Health.</p>
      </div>

      <div class="toggle" aria-label="Toggle front/back (Lucent)">
        <button type="button" class="active" id="lucentFrontBtn" onclick="showSide('lucent','front')">Front</button>
        <button type="button" id="lucentBackBtn" onclick="showSide('lucent','back')">Back</button>
      </div>
    </div>

    <div class="layout">

      <!-- LUCENT FRONT -->
      <div class="image-wrap" id="lucentFrontWrap">
        <div class="img-frame">
          <img
            src="https://hphealthplan.com/wp-content/uploads/2026/02/Lucent-Card-front-png.png"
            alt="Lucent Health ID Card Front"
          />
        </div>

        <div class="pin" style="--px: 2%; --py: 22%;" data-tx="24" data-ty="24">
          <button type="button" onclick="showInfo('lucent',1)">1</button>
        </div>

        <div class="pin" style="--px: 98%; --py: 22%;" data-tx="74" data-ty="24">
          <button type="button" onclick="showInfo('lucent',2)">2</button>
        </div>

        <div class="pin" style="--px: 98%; --py: 70%;" data-tx="74" data-ty="66">
          <button type="button" onclick="showInfo('lucent',3)">3</button>
        </div>

        <!-- UPDATED: #4 moved down to Rx info -->
        <div class="pin" style="--px: 2%; --py: 82%;" data-tx="28" data-ty="82">
          <button type="button" onclick="showInfo('lucent',4)">4</button>
        </div>
      </div>

      <!-- LUCENT BACK -->
      <div class="image-wrap" id="lucentBackWrap" style="display:none;">
        <div class="img-frame">
          <img
            src="https://hphealthplan.com/wp-content/uploads/2026/02/Lucent-Card-back-png.png"
            alt="Lucent Health ID Card Back"
          />
        </div>

        <div class="pin" style="--px: 2%; --py: 30%;" data-tx="26" data-ty="34">
          <button type="button" onclick="showInfo('lucent',5)">5</button>
        </div>

        <div class="pin" style="--px: 2%; --py: 84%;" data-tx="24" data-ty="80">
          <button type="button" onclick="showInfo('lucent',6)">6</button>
        </div>

        <div class="pin" style="--px: 98%; --py: 84%;" data-tx="62" data-ty="80">
          <button type="button" onclick="showInfo('lucent',7)">7</button>
        </div>

        <!-- NEW: #8 Eligibility & Benefits (top right) -->
        <div class="pin" style="--px: 98%; --py: 18%;" data-tx="78" data-ty="18">
          <button type="button" onclick="showInfo('lucent',8)">8</button>
        </div>
      </div>

      <!-- LUCENT PANEL -->
      <aside class="panel" id="lucentPanel">
        <h3>Click a number on the card</h3>
        <p>We’ll explain what that section is for, plus tips to avoid common issues (billing delays, eligibility confusion, etc.).</p>
        <div class="tip">
          <strong>Quick tip:</strong> If a provider’s office is confused, have them call the provider/customer service number on the back of the card.
        </div>
        <div class="mini">This page is an educational example and does not replace real-time eligibility/benefit verification.</div>
      </aside>

    </div>

    <div class="divider"></div>
    <!-- Note removed -->
  </section>

</div>

<script>
  // ---------- FRONT/BACK TOGGLE ----------
  function showSide(prefix, side){
    const frontWrap = document.getElementById(prefix + "FrontWrap");
    const backWrap  = document.getElementById(prefix + "BackWrap");
    const frontBtn  = document.getElementById(prefix + "FrontBtn");
    const backBtn   = document.getElementById(prefix + "BackBtn");

    if(side === "front"){
      frontWrap.style.display = "";
      backWrap.style.display = "none";
      frontBtn.classList.add("active");
      backBtn.classList.remove("active");
    } else {
      frontWrap.style.display = "none";
      backWrap.style.display = "";
      backBtn.classList.add("active");
      frontBtn.classList.remove("active");
    }

    // redraw leader lines after visibility changes
    requestAnimationFrame(drawLeaderLines);
  }

  // ---------- EXPLANATIONS ----------
  const content = {
    hpi: {
      1: {
        title: "1) Member & Group Information",
        text: "This box identifies the member and the employer group. Providers use the Member ID and Group Number to confirm eligibility and benefits.",
        tip: "If a clinic says they “can’t find you,” confirm they are using the Member ID exactly as shown (including letters), and that they’re using the correct payer/administrator contacts.  A common problem is a healthcare provider will look to verify your coverage with a network directly (ie: Aetna or First Health), but networks do not verify benefits, HPHP Concierge or the TPA must verify benefits and eligibility."
      },
      2: {
        title: "2) Medical Cost Share",
        text: "This section summarizes your copays/coinsurance, deductibles, and out-of-pocket limits depending on if you are seeing a Tier One provider vs. a Tier Two provider. Tier One benefits apply to Tier One healthcare providers, and Tier Two benefits apply to Tier Two healthcare providers.  Tier Three benefits are applicable OUT OF NETWORK.",
        tip: "When you can, choose Tier 1 providers for the best member experience and lowest out of pocket cost for you. If your provider is Tier 2, it is still in network. You may seek care from Tier One and/or Tier Two healthcare providers anytime.  All are considered in network, Tier One is simply a preferred network."
      },
      3: {
        title: "3) Network / Tier Configuration",
        text: "This area explains what Tier 1 and Tier 2 mean and which network(s) apply. Your card indicates Tier 1 is the preferred provider tier and Tier 2 uses First Health Network (with Tier 3 out-of-network).",
        tip: "Important: do not verify eligibility/benefits through First Health Network—eligibility and benefits are administered by High Plains Health plan and Health Plans, Inc. (HPI).  Healthcare providers may call HPHP Concierge at 806-510-HPHP(4747)."
      },
      4: {
        title: "4) Pharmacy Information",
        text: "Pharmacies use the routing information here (e.g., BIN/PCN/Group) to process prescriptions correctly.",
        tip: "If a prescription rejects at the counter, ask the pharmacist to re-check the BIN/PCN and confirm they’re using the member’s pharmacy info from this exact card."
      },
      5: {
        title: "5) Member Support / Contact Information",
        text: "This section lists key phone numbers and/or links for member help—questions about coverage, finding a provider, or getting assistance.",
        tip: "If you’re stuck between the provider’s billing office and the plan, call this number first. It’s usually faster than letting the provider guess."
      },
      6: {
        title: "6) Precertification / Prior Authorization",
        text: "Certain services may require precertification (prior authorization). Not completing it can cause delays or reduce coverage in some situations.",
        tip: "Before scheduling surgery, advanced imaging, or certain outpatient procedures, call to confirm whether precertification is required."
      },
      7: {
        title: "7) Claims Submission / Payor ID",
        text: "Providers use this information to submit claims to the correct administrator/payer and include the correct Payor ID.",
        tip: "If a provider says “we don’t know where to bill,” point them to this section and ask them to use the listed Payor ID and claims address."
      }
    },

    lucent: {
      1: {
        title: "1) Member & Group Information",
        text: "This box identifies the member and the employer group. Providers use the Member ID and Group Number to confirm eligibility and benefits.",
        tip: "If a clinic says they “can’t find you,” confirm they are using the Member ID exactly as shown (including letters), and that they’re using the correct payer/administrator contacts.  A common problem is a healthcare provider will look to verify your coverage with a network directly (ie: Aetna or First Health), but networks do not verify benefits, HPHP Concierge or the TPA must verify benefits and eligibility."
      },
      2: {
        title: "2) High Plains Health Plan Tier One Network",
        text: "This area explains that Tier 1 is the HPHP direct network. Tier One benefits are applicable at Tier One healthcare providers.  You can search this network directory at www.hphealthplan.com/directory",
        tip: "When you can, choose Tier 1 providers for the best member experience and lowest cost for you. If your provider is Tier 2, it is still in network.  You may seek care from Tier One and/or Tier Two healthcare providers anytime.  All are considered in network, Tier One is simply a preferred network."
      },
      3: {
        title: "3) Tier Two Wrap Network",
        text: "This area identifies the Tier Two network being used alongside Tier One. Healthcare providers who participate in the identified Tier Two network are IN NETWORK WITH HPHP.",
        tip: "If a provider’s office is not sure about network status, please ask them to contact HPHP Concierge for quick confirmation.  806-510-HPHP(4747).  If and when a healthcare provider participates in both Tier One and Tier Two networks, Tier One Network is primary."
      },
      4: {
        title: "4) Pharmacy Information",
        text: "Pharmacies use the routing information here (e.g., BIN/PCN/Group) to process prescriptions correctly.",
        tip: "If a prescription rejects at the counter, ask the pharmacist to re-check the BIN/PCN and confirm they’re using the member’s pharmacy info from this exact card."
      },
      5: {
        title: "5) Claims Submission / Payor ID",
        text: "Providers use this information to submit claims to the correct administrator/payer and include the correct Payor ID.",
        tip: "If a provider says “we don’t know where to bill,” point them to this section and ask them to use the listed Payor ID and claims address."
      },
      6: {
        title: "6) Coverage",
        text: "This area explains the member's coverage level and effective date of coverage.",
        tip: "Dependents may not be individually listed in this section."
      },
      7: {
        title: "7) Precertification/Teledoc",
        text: "Precertification is required for specific medical services.  Healthcare providers must call this number to initiate precertification of those services.",
        tip: "Precertification is generally required for things like hospital admissions, certain outpatient surgeries, diagnostic imaging (CT/MRI), and all specialty medications.  Have physicians request precertification well in advance so that your care is not delayed due to not have it precertified."
      },
      8: {
        title: "8) Eligibility & Benefits",
        text: "This section is where providers should call to verify eligibility and benefits before care is provided.",
        tip: "If a provider tries to verify through a network, redirect them here (or to HPHP Concierge if instructed). Networks do not verify eligibility/benefits."
      }
    }
  };

  // ---------- PANEL UPDATE ----------
  function showInfo(prefix, sectionId){
    const panel = document.getElementById(prefix + "Panel");
    const item = content[prefix] && content[prefix][sectionId];

    if(!item){
      panel.innerHTML = "<h3>Not found</h3><p>That section hasn’t been configured yet.</p>";
      return;
    }

    panel.innerHTML = `
      <h3>${item.title}</h3>
      <p>${item.text}</p>
      <div class="tip"><strong>Tip:</strong> ${item.tip}</div>
      <div class="mini">Educational example. For exact benefits, use real-time eligibility verification.</div>
    `;

    if (window.innerWidth < 980) {
      panel.scrollIntoView({ behavior: "smooth", block: "start" });
    }
  }

  // ---------- LEADER LINE DRAWING ----------
  function drawLeaderLines(){
    const wraps = document.querySelectorAll(".image-wrap");
    wraps.forEach(wrap => {
      if (getComputedStyle(wrap).display === "none") return;

      const pins = wrap.querySelectorAll(".pin");
      const wrapRect = wrap.getBoundingClientRect();

      pins.forEach(pin => {
        const pinRect = pin.getBoundingClientRect();

        // pin center relative to wrap
        const px = (pinRect.left + pinRect.width/2) - wrapRect.left;
        const py = (pinRect.top + pinRect.height/2) - wrapRect.top;

        // target is stored as % of wrap
        const txPct = parseFloat(pin.dataset.tx);
        const tyPct = parseFloat(pin.dataset.ty);

        const tx = (txPct / 100) * wrapRect.width;
        const ty = (tyPct / 100) * wrapRect.height;

        const dx = tx - px;
        const dy = ty - py;

        const len = Math.max(18, Math.sqrt(dx*dx + dy*dy));
        const ang = Math.atan2(dy, dx) * (180/Math.PI);

        pin.style.setProperty("--len", len.toFixed(1) + "px");
        pin.style.setProperty("--ang", ang.toFixed(2) + "deg");
      });
    });
  }

  window.addEventListener("load", drawLeaderLines);
  window.addEventListener("resize", drawLeaderLines);
</script>

</body>
</html>
