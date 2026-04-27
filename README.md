
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Historia Clínica — Formulario de Ingreso</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #faf8f5;
    --white: #ffffff;
    --gold: #b8966e;
    --gold-light: #d4b896;
    --dark: #1a1714;
    --mid: #4a4540;
    --soft: #8a8078;
    --border: #ddd8d0;
    --accent-bg: #f5f0e8;
    --warning: #8b3a2a;
    --warning-bg: #fdf0ec;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--cream);
    color: var(--dark);
    font-size: 11pt;
    line-height: 1.6;
  }

  .page {
    max-width: 820px;
    margin: 0 auto;
    background: var(--white);
    padding: 48px 56px;
  }

  /* HEADER */
  .header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 2px solid var(--gold);
    padding-bottom: 20px;
    margin-bottom: 28px;
  }
  .header-left h1 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 28pt;
    font-weight: 300;
    color: var(--dark);
    letter-spacing: 0.02em;
  }
  .header-left p {
    font-size: 9pt;
    color: var(--soft);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin-top: 2px;
  }
  .header-right {
    text-align: right;
    font-size: 8.5pt;
    color: var(--soft);
  }
  .header-right .date-field {
    display: inline-block;
    border-bottom: 1px solid var(--border);
    min-width: 130px;
    margin-left: 6px;
  }

  /* SECTIONS */
  .section {
    margin-bottom: 24px;
  }
  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 14pt;
    font-weight: 600;
    color: var(--gold);
    border-bottom: 1px solid var(--border);
    padding-bottom: 5px;
    margin-bottom: 14px;
    letter-spacing: 0.03em;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-title .num {
    background: var(--gold);
    color: white;
    font-family: 'DM Sans', sans-serif;
    font-size: 9pt;
    font-weight: 500;
    width: 22px;
    height: 22px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }

  /* GRID FIELDS */
  .fields-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px 24px;
  }
  .fields-grid.three { grid-template-columns: 1fr 1fr 1fr; }
  .fields-grid.full { grid-template-columns: 1fr; }

  .field {
    display: flex;
    flex-direction: column;
    gap: 3px;
  }
  .field.span2 { grid-column: span 2; }
  .field label {
    font-size: 8pt;
    font-weight: 500;
    color: var(--soft);
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }
  .field input[type="text"],
  .field input[type="date"],
  .field textarea {
    border: none;
    border-bottom: 1px solid var(--border);
    background: transparent;
    padding: 4px 2px;
    font-family: 'DM Sans', sans-serif;
    font-size: 10.5pt;
    color: var(--dark);
    outline: none;
    width: 100%;
  }
  .field textarea {
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 8px;
    resize: vertical;
    min-height: 52px;
    margin-top: 2px;
  }
  .field input[type="text"]:focus,
  .field input[type="date"]:focus,
  .field textarea:focus {
    border-color: var(--gold);
  }

  /* CHECKBOXES */
  .check-group {
    display: flex;
    flex-wrap: wrap;
    gap: 8px 20px;
    margin-top: 6px;
  }
  .check-item {
    display: flex;
    align-items: center;
    gap: 6px;
    cursor: pointer;
    font-size: 10pt;
    color: var(--mid);
  }
  .check-item input[type="checkbox"] {
    width: 14px;
    height: 14px;
    accent-color: var(--gold);
    cursor: pointer;
    flex-shrink: 0;
  }

  /* SUBSECTION */
  .subsection {
    background: var(--accent-bg);
    border-left: 3px solid var(--gold-light);
    border-radius: 0 6px 6px 0;
    padding: 12px 16px;
    margin-bottom: 12px;
  }
  .subsection-title {
    font-size: 9.5pt;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--gold);
    margin-bottom: 10px;
  }

  /* SATISFACCIÓN */
  .satisfaction {
    display: flex;
    gap: 8px;
    margin-top: 4px;
    flex-wrap: wrap;
  }
  .satisfaction label {
    display: flex;
    align-items: center;
    gap: 4px;
    font-size: 10pt;
    color: var(--mid);
    cursor: pointer;
  }
  .satisfaction input[type="radio"] {
    accent-color: var(--gold);
    cursor: pointer;
  }

  /* WARNING BOX */
  .warning-box {
    background: var(--warning-bg);
    border: 1.5px solid #d4856a;
    border-radius: 8px;
    padding: 20px 22px;
    margin-bottom: 20px;
  }
  .warning-box .warning-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 13pt;
    font-weight: 600;
    color: var(--warning);
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .warning-item {
    display: flex;
    gap: 10px;
    margin-bottom: 10px;
    align-items: flex-start;
  }
  .warning-item .dot {
    width: 7px;
    height: 7px;
    background: var(--warning);
    border-radius: 50%;
    flex-shrink: 0;
    margin-top: 5px;
  }
  .warning-item p {
    font-size: 10pt;
    color: var(--mid);
    line-height: 1.5;
  }
  .warning-item strong {
    color: var(--warning);
  }

  /* DECLARATION */
  .declaration-box {
    border: 1.5px solid var(--gold);
    border-radius: 8px;
    padding: 18px 22px;
    margin-bottom: 20px;
    background: var(--accent-bg);
  }
  .declaration-box p {
    font-size: 10pt;
    color: var(--mid);
    line-height: 1.7;
    font-style: italic;
  }

  /* FIRMA DIGITAL */
  .firma-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-top: 16px;
  }
  .firma-field {
    display: flex;
    flex-direction: column;
    gap: 6px;
  }
  .firma-field label {
    font-size: 8pt;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--soft);
    font-weight: 500;
  }
  .firma-line {
    border-bottom: 1.5px solid var(--dark);
    height: 42px;
    position: relative;
  }
  .sig-wrapper {
    position: relative;
    border: 1.5px solid var(--border);
    border-radius: 6px;
    background: #fdfcfa;
    overflow: hidden;
  }
  .sig-wrapper canvas {
    display: block;
    width: 100%;
    height: 120px;
    touch-action: none;
    cursor: crosshair;
  }
  .sig-placeholder {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 9pt;
    color: var(--border);
    pointer-events: none;
    white-space: nowrap;
    transition: opacity 0.3s;
  }
  .sig-controls {
    display: flex;
    justify-content: flex-end;
    gap: 8px;
    margin-top: 5px;
  }
  .sig-btn {
    font-family: 'DM Sans', sans-serif;
    font-size: 8pt;
    padding: 4px 12px;
    border-radius: 3px;
    cursor: pointer;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--soft);
    transition: all 0.2s;
  }
  .sig-btn:hover { border-color: var(--gold); color: var(--gold); }
  .sig-btn.signed { border-color: #5a8a5a; color: #5a8a5a; pointer-events: none; }
  @media print {
    .sig-controls { display: none; }
    .sig-wrapper { border-color: #ccc; }
  }

  /* PRINT BUTTON */
  .print-bar {
    display: flex;
    gap: 12px;
    justify-content: flex-end;
    margin-bottom: 28px;
  }
  .btn {
    font-family: 'DM Sans', sans-serif;
    font-size: 9.5pt;
    font-weight: 500;
    letter-spacing: 0.06em;
    padding: 9px 22px;
    border-radius: 4px;
    cursor: pointer;
    border: none;
    text-transform: uppercase;
    transition: opacity 0.2s;
  }
  .btn:hover { opacity: 0.82; }
  .btn-primary {
    background: var(--gold);
    color: white;
  }
  .btn-outline {
    background: transparent;
    color: var(--gold);
    border: 1.5px solid var(--gold);
  }

  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 20px 0;
  }

  .inline-fields {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
  }
  .inline-fields .field {
    flex: 1;
    min-width: 140px;
  }

  /* PRINT STYLES */
  @media print {
    .print-bar { display: none; }
    body { background: white; }
    .page { padding: 28px 36px; box-shadow: none; }
    .field input, .field textarea { border-color: #ccc !important; }
    .warning-box { border-color: #c07060 !important; }
  }
</style>
</head>
<body>

<div class="page">

  <!-- PRINT BAR -->
  <div class="print-bar">
    <button class="btn btn-outline" onclick="window.print()">🖨 Imprimir</button>
    <button class="btn btn-primary" onclick="downloadForm()">⬇ Descargar PDF</button>
  </div>

  <!-- HEADER -->
  <div class="header">
    <div class="header-left">
      <h1>Historia Clínica</h1>
      <p>Formulario de Ingreso — Confidencial</p>
    </div>
    <div class="header-right">
      Fecha de consulta:<span class="date-field"></span><br>
      No. Historia:<span class="date-field"></span>
    </div>
  </div>

  <!-- 1. DATOS PERSONALES -->
  <div class="section">
    <div class="section-title"><span class="num">1</span> Datos Personales</div>
    <div class="fields-grid">
      <div class="field span2">
        <label>Nombre completo</label>
        <input type="text" placeholder="">
      </div>
      <div class="field">
        <label>Teléfono / Celular</label>
        <input type="text" placeholder="">
      </div>
      <div class="field">
        <label>Correo electrónico</label>
        <input type="text" placeholder="">
      </div>
      <div class="field">
        <label>Fecha de nacimiento</label>
        <input type="date">
      </div>
      <div class="field">
        <label>Cédula / ID</label>
        <input type="text" placeholder="">
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- 2. ANTECEDENTES PATOLÓGICOS -->
  <div class="section">
    <div class="section-title"><span class="num">2</span> Antecedentes Personales Patológicos</div>
    <div class="check-group">
      <label class="check-item"><input type="checkbox"> Diabetes</label>
      <label class="check-item"><input type="checkbox"> Hipertensión</label>
      <label class="check-item"><input type="checkbox"> Enfermedades cardíacas</label>
      <label class="check-item"><input type="checkbox"> Enfermedades pulmonares</label>
      <label class="check-item"><input type="checkbox"> Enfermedades renales</label>
      <label class="check-item"><input type="checkbox"> Enfermedades hepáticas</label>
      <label class="check-item"><input type="checkbox"> Trastornos de coagulación</label>
      <label class="check-item"><input type="checkbox"> Enfermedades autoinmunes</label>
      <label class="check-item"><input type="checkbox"> Cáncer</label>
      <label class="check-item"><input type="checkbox"> Trastornos de tiroides</label>
      <label class="check-item"><input type="checkbox"> VIH / Hepatitis</label>
      <label class="check-item"><input type="checkbox"> Otros</label>
    </div>
    <div class="field" style="margin-top:10px;">
      <label>Especificar / Observaciones</label>
      <textarea placeholder="Indique diagnósticos, tratamientos actuales, médico tratante..."></textarea>
    </div>
  </div>

  <hr class="divider">

  <!-- 3. ANTECEDENTES NO PATOLÓGICOS -->
  <div class="section">
    <div class="section-title"><span class="num">3</span> Antecedentes Personales No Patológicos</div>
    <div class="check-group">
      <label class="check-item"><input type="checkbox"> Tabaquismo</label>
      <label class="check-item"><input type="checkbox"> Alcoholismo</label>
      <label class="check-item"><input type="checkbox"> Consumo de drogas psicoactivas</label>
      <label class="check-item"><input type="checkbox"> Sedentarismo</label>
      <label class="check-item"><input type="checkbox"> Actividad física regular</label>
      <label class="check-item"><input type="checkbox"> Dietas restrictivas</label>
      <label class="check-item"><input type="checkbox"> Ninguno</label>
    </div>
    <div class="field" style="margin-top:10px;">
      <label>Tipo de droga / frecuencia / cantidad (si aplica)</label>
      <textarea placeholder="Detalle sustancia, frecuencia de consumo y última vez..."></textarea>
    </div>
  </div>

  <hr class="divider">

  <!-- 4. ANTICONCEPTIVOS -->
  <div class="section">
    <div class="section-title"><span class="num">4</span> Anticonceptivos</div>
    <div class="check-group">
      <label class="check-item"><input type="checkbox"> Pastillas anticonceptivas</label>
      <label class="check-item"><input type="checkbox"> Inyección anticonceptiva</label>
      <label class="check-item"><input type="checkbox"> Implante subdérmico</label>
      <label class="check-item"><input type="checkbox"> DIU hormonal</label>
      <label class="check-item"><input type="checkbox"> DIU de cobre</label>
      <label class="check-item"><input type="checkbox"> Parche anticonceptivo</label>
      <label class="check-item"><input type="checkbox"> Preservativo (solo)</label>
      <label class="check-item"><input type="checkbox"> Ligadura de trompas</label>
      <label class="check-item"><input type="checkbox"> Ninguno</label>
    </div>
    <div class="field" style="margin-top:10px;">
      <label>Nombre del medicamento / fecha última dosis</label>
      <input type="text" placeholder="">
    </div>
  </div>

  <hr class="divider">

  <!-- 5. ALERGIAS -->
  <div class="section">
    <div class="section-title"><span class="num">5</span> Alergias a Medicamentos o Alimentos</div>
    <div class="check-group">
      <label class="check-item"><input type="checkbox"> Penicilina / Amoxicilina</label>
      <label class="check-item"><input type="checkbox"> Sulfas</label>
      <label class="check-item"><input type="checkbox"> AINES (ibuprofeno, diclofenaco)</label>
      <label class="check-item"><input type="checkbox"> Anestésicos locales</label>
      <label class="check-item"><input type="checkbox"> Látex</label>
      <label class="check-item"><input type="checkbox"> Yodo / Povidona</label>
      <label class="check-item"><input type="checkbox"> Mariscos / Pescado</label>
      <label class="check-item"><input type="checkbox"> Gluten</label>
      <label class="check-item"><input type="checkbox"> Otro alimento</label>
      <label class="check-item"><input type="checkbox"> Ninguna alergia conocida</label>
    </div>
    <div class="field" style="margin-top:10px;">
      <label>Especificar alergia y tipo de reacción</label>
      <textarea placeholder="Medicamento o alimento — Reacción presentada (erupción, dificultad para respirar, anafilaxia...)"></textarea>
    </div>
  </div>

  <hr class="divider">

  <!-- 6. ANTECEDENTES GINECOLÓGICOS -->
  <div class="section">
    <div class="section-title"><span class="num">6</span> Antecedentes Ginecológicos</div>
    <div class="fields-grid three">
      <div class="field">
        <label>Fecha última menstruación</label>
        <input type="date">
      </div>
      <div class="field">
        <label>Ciclos menstruales</label>
        <input type="text" placeholder="Regulares / Irregulares">
      </div>
      <div class="field">
        <label>Última citología / Papanicolau</label>
        <input type="text" placeholder="Fecha y resultado">
      </div>
    </div>
    <div class="check-group" style="margin-top:10px;">
      <label class="check-item"><input type="checkbox"> Embarazo actual</label>
      <label class="check-item"><input type="checkbox"> Lactancia</label>
      <label class="check-item"><input type="checkbox"> Endometriosis</label>
      <label class="check-item"><input type="checkbox"> Miomas / Quistes</label>
      <label class="check-item"><input type="checkbox"> SOP (Síndrome Ovario Poliquístico)</label>
      <label class="check-item"><input type="checkbox"> Menopausia</label>
      <label class="check-item"><input type="checkbox"> Ninguno</label>
    </div>
    <div class="fields-grid" style="margin-top:10px;">
      <div class="field">
        <label>Número de embarazos (gestas)</label>
        <input type="text" placeholder="">
      </div>
      <div class="field">
        <label>Número de partos / cesáreas</label>
        <input type="text" placeholder="">
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- 7. ANTECEDENTES QUIRÚRGICOS -->
  <div class="section">
    <div class="section-title"><span class="num">7</span> Antecedentes Quirúrgicos</div>

    <div class="subsection">
      <div class="subsection-title">A · Cirugías de Salud / Médicas</div>
      <div class="check-group">
        <label class="check-item"><input type="checkbox"> Apendicectomía</label>
        <label class="check-item"><input type="checkbox"> Colecistectomía</label>
        <label class="check-item"><input type="checkbox"> Cesárea</label>
        <label class="check-item"><input type="checkbox"> Histerectomía</label>
        <label class="check-item"><input type="checkbox"> Cirugía cardíaca</label>
        <label class="check-item"><input type="checkbox"> Cirugía ortopédica</label>
        <label class="check-item"><input type="checkbox"> Bariatría / Manga gástrica</label>
        <label class="check-item"><input type="checkbox"> Otra</label>
        <label class="check-item"><input type="checkbox"> Ninguna</label>
      </div>
      <div class="field" style="margin-top:10px;">
        <label>Detalles (tipo, año, complicaciones)</label>
        <textarea placeholder="Describa las cirugías, año en que se realizaron y si hubo alguna complicación..."></textarea>
      </div>
    </div>

    <div class="subsection">
      <div class="subsection-title">B · Cirugías Estéticas / Plásticas Previas</div>
      <div class="check-group">
        <label class="check-item"><input type="checkbox"> Rinoplastia</label>
        <label class="check-item"><input type="checkbox"> Mamoplastia (aumento)</label>
        <label class="check-item"><input type="checkbox"> Mamoplastia (reducción)</label>
        <label class="check-item"><input type="checkbox"> Liposucción</label>
        <label class="check-item"><input type="checkbox"> Abdominoplastia</label>
        <label class="check-item"><input type="checkbox"> Bichectomía</label>
        <label class="check-item"><input type="checkbox"> Blefaroplastia</label>
        <label class="check-item"><input type="checkbox"> Lifting facial</label>
        <label class="check-item"><input type="checkbox"> BBL (lipotransferencia glútea)</label>
        <label class="check-item"><input type="checkbox"> Otra</label>
        <label class="check-item"><input type="checkbox"> Ninguna</label>
      </div>
      <div class="fields-grid" style="margin-top:12px;">
        <div class="field">
          <label>Ciudad / País donde se realizó</label>
          <input type="text" placeholder="">
        </div>
        <div class="field">
          <label>Fecha (aproximada)</label>
          <input type="text" placeholder="Mes / Año">
        </div>
        <div class="field span2">
          <label>Nombre del cirujano que la realizó</label>
          <input type="text" placeholder="">
        </div>
      </div>
      <div class="field" style="margin-top:10px;">
        <label>¿Nivel de satisfacción con la cirugía anterior?</label>
        <div class="satisfaction">
          <label><input type="radio" name="satisfaccion" value="muy-satisfecha"> 😊 Muy satisfecha</label>
          <label><input type="radio" name="satisfaccion" value="satisfecha"> 🙂 Satisfecha</label>
          <label><input type="radio" name="satisfaccion" value="regular"> 😐 Regular</label>
          <label><input type="radio" name="satisfaccion" value="insatisfecha"> 😕 Insatisfecha</label>
          <label><input type="radio" name="satisfaccion" value="muy-insatisfecha"> 😟 Muy insatisfecha</label>
        </div>
      </div>
      <div class="field" style="margin-top:10px;">
        <label>¿Por qué? (opcional)</label>
        <textarea placeholder="Comparta cualquier observación sobre el resultado previo..."></textarea>
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- 8. INDICACIONES IMPORTANTES -->
  <div class="warning-box">
    <div class="warning-title">
      ⚠️ Indicaciones Importantes — Por favor leer con atención
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Anticonceptivos hormonales (pastillas, inyección, parche):</strong> Deben suspenderse <strong>mínimo 2 semanas antes</strong> de la cirugía. Solo podrán retomarse <strong>después de 1 mes</strong> de la recuperación. Informe siempre a su médico.</p>
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Cigarrillo y drogas:</strong> Están <strong>estrictamente prohibidos</strong> tanto antes de la cirugía como durante todo el período de recuperación. Su consumo puede causar complicaciones graves y comprometer el resultado.</p>
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Alcohol:</strong> Debe suspenderse <strong>mínimo 1 semana antes</strong> de la cirugía.</p>
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Viajes y cargas pesadas:</strong> Cualquier tipo de viaje y el levantamiento de objetos pesados deben suspenderse durante <strong>1 a 2 meses después</strong> de la cirugía, según indicación médica.</p>
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Déficit nutricional:</strong> Si presenta anemia, deficiencia de vitaminas u otras condiciones nutricionales, <strong>debe informarlo al médico</strong> antes del procedimiento. Estas condiciones pueden afectar la cicatrización y la recuperación.</p>
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Presupuesto:</strong> Los presupuestos presentados son <strong>aproximados y pueden variar</strong> en cualquier momento por situaciones alternas imprevistas.</p>
    </div>

    <div class="warning-item">
      <div class="dot"></div>
      <p><strong>Importante:</strong> El incumplimiento de cualquiera de estas indicaciones puede ser causa de <strong>cancelación o postergación de la cirugía</strong>, incluso en etapas previas o posteriores al procedimiento.</p>
    </div>
  </div>

  <!-- 9. DECLARACIÓN -->
  <div class="declaration-box">
    <p>
      Yo, el/la abajo firmante, declaro que la información proporcionada en este formulario es verídica y completa a mi mejor conocimiento. 
      <strong>Entiendo plenamente que no seguir las indicaciones médicas aquí descritas puede comprometer todas las etapas del proceso quirúrgico</strong>, 
      tanto las previas como las posteriores a la cirugía, y que el equipo médico puede tomar las decisiones que considere pertinentes para garantizar mi seguridad. 
      Igualmente entiendo que los presupuestos son aproximados y sujetos a cambios.
      He leído, comprendido y acepto las indicaciones establecidas en este documento.
    </p>
  </div>

  <!-- 10. FIRMA DIGITAL -->
  <div class="section">
    <div class="section-title"><span class="num">&#10022;</span> Firma Digital y Aceptación</div>

    <div class="firma-grid">
      <div class="firma-field">
        <label>Nombre completo del paciente</label>
        <input type="text" id="nombreFirma" style="border:none;border-bottom:1.5px solid var(--border);padding:4px 2px;font-family:'DM Sans',sans-serif;font-size:10.5pt;outline:none;width:100%;" placeholder="">
      </div>
      <div class="firma-field">
        <label>C&eacute;dula / ID</label>
        <input type="text" id="cedulaFirma" style="border:none;border-bottom:1.5px solid var(--border);padding:4px 2px;font-family:'DM Sans',sans-serif;font-size:10.5pt;outline:none;width:100%;" placeholder="">
      </div>
    </div>

    <div style="margin-top:20px;">
      <div class="firma-field">
        <label>Firma digital &mdash; Dibuje su firma con el dedo o el mouse</label>
        <div class="sig-wrapper">
          <canvas id="sigCanvas"></canvas>
          <span class="sig-placeholder" id="sigPlaceholder">&#9997; Firme aqu&iacute;</span>
        </div>
        <div class="sig-controls">
          <button class="sig-btn" id="clearBtn" onclick="clearSignature()">&#10005; Borrar firma</button>
          <button class="sig-btn" id="confirmBtn" onclick="confirmSignature()">&#10004; Confirmar firma</button>
        </div>
      </div>
    </div>

    <div style="margin-top:14px; max-width:220px;">
      <div class="firma-field">
        <label>Fecha y hora de firma</label>
        <input type="text" id="fechaFirma" style="border:none;border-bottom:1.5px solid var(--border);padding:4px 2px;font-family:'DM Sans',sans-serif;font-size:10.5pt;outline:none;width:100%;color:var(--mid);" readonly>
      </div>
    </div>
  </div>

</div><!-- end .page -->

<script>
// DATE
document.addEventListener('DOMContentLoaded', () => {
  const dateFields = document.querySelectorAll('.date-field');
  const today = new Date().toLocaleDateString('es-CO', {day:'2-digit', month:'2-digit', year:'numeric'});
  if (dateFields[0]) dateFields[0].textContent = ' ' + today;
});

// SIGNATURE PAD
const canvas = document.getElementById('sigCanvas');
const ctx = canvas.getContext('2d');
let drawing = false;
let hasSigned = false;

function resizeCanvas() {
  const wrapper = canvas.parentElement;
  const ratio = window.devicePixelRatio || 1;
  const w = wrapper.offsetWidth;
  canvas.width = w * ratio;
  canvas.height = 120 * ratio;
  canvas.style.width = w + 'px';
  canvas.style.height = '120px';
  ctx.scale(ratio, ratio);
  ctx.strokeStyle = '#1a1714';
  ctx.lineWidth = 2.2;
  ctx.lineCap = 'round';
  ctx.lineJoin = 'round';
}
resizeCanvas();
window.addEventListener('resize', resizeCanvas);

function getPos(e) {
  const rect = canvas.getBoundingClientRect();
  const ratio = window.devicePixelRatio || 1;
  const src = e.touches ? e.touches[0] : e;
  return {
    x: (src.clientX - rect.left),
    y: (src.clientY - rect.top)
  };
}

canvas.addEventListener('mousedown', e => {
  drawing = true;
  const p = getPos(e);
  ctx.beginPath();
  ctx.moveTo(p.x, p.y);
});
canvas.addEventListener('mousemove', e => {
  if (!drawing) return;
  const p = getPos(e);
  ctx.lineTo(p.x, p.y);
  ctx.stroke();
  showSigned();
});
canvas.addEventListener('mouseup', () => { drawing = false; });
canvas.addEventListener('mouseleave', () => { drawing = false; });

canvas.addEventListener('touchstart', e => {
  e.preventDefault();
  drawing = true;
  const p = getPos(e);
  ctx.beginPath();
  ctx.moveTo(p.x, p.y);
}, {passive: false});
canvas.addEventListener('touchmove', e => {
  e.preventDefault();
  if (!drawing) return;
  const p = getPos(e);
  ctx.lineTo(p.x, p.y);
  ctx.stroke();
  showSigned();
}, {passive: false});
canvas.addEventListener('touchend', () => { drawing = false; });

function showSigned() {
  hasSigned = true;
  document.getElementById('sigPlaceholder').style.opacity = '0';
}

function clearSignature() {
  const ratio = window.devicePixelRatio || 1;
  ctx.clearRect(0, 0, canvas.width / ratio, canvas.height / ratio);
  hasSigned = false;
  document.getElementById('sigPlaceholder').style.opacity = '1';
  const btn = document.getElementById('confirmBtn');
  btn.className = 'sig-btn';
  btn.textContent = '\u2714 Confirmar firma';
  document.getElementById('fechaFirma').value = '';
  canvas.style.pointerEvents = 'auto';
  canvas.style.opacity = '1';
}

function confirmSignature() {
  if (!hasSigned) {
    alert('Por favor dibuje su firma antes de confirmar.');
    return;
  }
  const now = new Date().toLocaleString('es-CO', {
    day: '2-digit', month: '2-digit', year: 'numeric',
    hour: '2-digit', minute: '2-digit'
  });
  document.getElementById('fechaFirma').value = now;
  const btn = document.getElementById('confirmBtn');
  btn.textContent = '\u2714 Firma confirmada';
  btn.className = 'sig-btn signed';
  canvas.style.pointerEvents = 'none';
  canvas.style.opacity = '0.85';
  // Draw green checkmark hint on canvas edge
  ctx.font = '11px DM Sans, sans-serif';
  ctx.fillStyle = '#5a8a5a';
  ctx.fillText('Firma confirmada \u2714', 8, canvas.height / (window.devicePixelRatio||1) - 8);
}

function downloadForm() {
  if (!hasSigned) {
    if (!confirm('No ha dibujado su firma. \u00BFDesea continuar de todas formas?')) return;
  }
  window.print();
}
</script>
</body>
</html>
