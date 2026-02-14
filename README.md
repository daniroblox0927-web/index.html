
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Estado del trámite del documento</title>

<style>
body{
    margin:0;
    font-family: Arial, Helvetica, sans-serif;
    background: linear-gradient(to bottom, #d7e9ea, #083b5c);
}

.container{
    max-width: 480px;
    margin: 40px auto;
    padding: 15px;
}

.header{
    text-align:center;
    margin-bottom:20px;
}

.header h1{
    font-size:16px;
    letter-spacing:1px;
    margin:0;
}

.header small{
    font-size:12px;
    color:#444;
}

.card{
    background:#f2f2f2;
    border-radius:25px;
    padding:20px;
    box-shadow:0 8px 20px rgba(0,0,0,0.1);
}

.input{
    width:100%;
    padding:12px;
    border-radius:30px;
    border:1px solid #aaa;
    margin:10px 0;
    font-size:14px;
}

.button{
    width:100%;
    padding:12px;
    border-radius:30px;
    border:none;
    background:#0b3a63;
    color:white;
    font-weight:bold;
    cursor:pointer;
    transition:0.3s;
}

.button:hover{
    background:#072a47;
}

.result{
    margin-top:20px;
    background:#e0e0e0;
    border-radius:15px;
    padding:15px;
    font-size:13px;
}

.label{
    font-weight:bold;
}

.info{
    margin-top:20px;
    background:#f2f2f2;
    border-radius:20px;
    padding:15px;
    font-size:12px;
}
</style>
</head>

<body>

<div class="container">

<div class="header">
<h1>ESTADO DEL TRÁMITE DEL DOCUMENTO DE IDENTIDAD</h1>
<small>Inicio / Consultar</small>
</div>

<div class="card">
<label>No. Identificación:</label>
<input type="text" id="cedula" class="input" placeholder="digite el número sin puntos ni comas">
<button class="button" onclick="consultar()">Consultar</button>
<div id="resultado"></div>
</div>

<div class="info">
<b>INFORMACIÓN</b><br><br>
Por favor digite su número de identidad y dé clic en el botón consultar.
</div>

</div>

<script>

// 🔥 BASE DE DATOS SIMULADA
const baseDatos = {
    "1016718262": {
        preparacion: "8509757521",
        fecha: "28 de Enero de 2026",
        oficina: "BOGOTÁ - CUNDINAMARCA",
        estado: "Su trámite se encuentra en verificación de información, validación y elaboración."
       
            "1013624088": {
    preparacion: "9999999999",
    fecha: "01 de Enero de 2025",
    oficina: "BARRANQUILLA - ATLÁNTICO",
    estado: "Documento en producción."
}

    },
    "123456215": {
        preparacion: "7745123698",
        fecha: "29 de julio de 2026",
        oficina: "BOGOTÁ - CUNDINAMARCA",
        estado: "Su documento está listo para ser reclamado en la oficina seleccionada."
    },
    "9876543210": {
        preparacion: "5587412369",
        fecha: "05 de Septiembre de 2024",
        oficina: "CALI - VALLE DEL CAUCA",
        estado: "El trámite fue rechazado por inconsistencias en la información."
    }
};

function consultar(){
    let cedula = document.getElementById("cedula").value;
    let resultado = document.getElementById("resultado");

    if(baseDatos[cedula]){
        let datos = baseDatos[cedula];

        resultado.innerHTML = `
        <div class="result">
        <div><span class="label">NO. DE PREPARACIÓN:</span> ${datos.preparacion}</div><br>
        <div><span class="label">FECHA:</span> ${datos.fecha}</div><br>
        <div><span class="label">OFICINA:</span> ${datos.oficina}</div><br><br>
        <div>${datos.estado}</div>
        </div>
        `;
    }else{
        resultado.innerHTML = `
        <div class="result">
        No se encontró información asociada al número ingresado.
        </div>
        `;
    }
}

</script>

</body>
</html>
