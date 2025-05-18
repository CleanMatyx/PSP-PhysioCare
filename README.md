
<H2>Contributors</H2>
<ul>
  <li>Matías E. Borra Quiroz</li>
  <li>Adrián Bermejo Naranjo</li>
  <li>Pablo García Sánchez-Fotún</li>
</ul>
<h2>Table of Contents</h2>
<ul>
  <li><a href="#overview">Overview</a></li>
  <li><a href="#features">🚀 Features</a></li>
  <li><a href="#technologies">🛠️ Technologies</a></li>
  <li><a href="#project-structure">📂 Project Structure</a></li>
  <li><a href="#installation">🎯 Installation</a></li>
  <li><a href="#contributing">🤝 Contributing</a></li>
  <li><a href="#license">📄 License</a></li>
</ul>

<hr>

<h2 id="overview">Overview</h2>
<p><strong>PSP-PhysioCare</strong> is a JavaFX desktop application designed to streamline the management of physiotherapy clinics. It offers secure authentication and full CRUD (Create, Read, Update, Delete) operations for both patients and physiotherapists through an intuitive graphical interface.</p>

<hr>
<h2>Backend</h2>
<p>https://github.com/CleanMatyx/PhysioCareWeb</p>
<hr>

<h2 id="features">🚀 Features</h2>
<ul>
  <li>
    <strong>User Authentication</strong><br>
    Secure login screen validating credentials against a REST API, with session token storage.
  </li>
  <li>
    <strong>Main Dashboard</strong><br>
    Navigation menu to manage Patients and Physiotherapists, with smooth JavaFX transitions.
  </li>
  <li>
    <strong>Patient Management</strong>
    <ul>
      <li>Searchable, paginated list of patients</li>
      <li>Add, edit &amp; delete patient records (Name, Surname, DOB, Address, Insurance No., Email)</li>
    </ul>
  </li>
  <li>
    <strong>Physiotherapist Management</strong>
    <ul>
      <li>Searchable list of physiotherapists</li>
      <li>Add, edit &amp; delete physiotherapist records (Name, Surname, Specialty, License No., Email)</li>
    </ul>
  </li>
</ul>

<hr>

<h2 id="technologies">🛠️ Technologies</h2>
<ul>
  <li><strong>Java 23</strong></li>
  <li><strong>JavaFX 21</strong></li>
  <li><strong>Maven Wrapper</strong> (<code>./mvnw</code> / <code>mvnw.cmd</code>)</li>
  <li><strong>Gson</strong> (JSON serialization/deserialization)</li>
  <li><strong>HTTPURLConnection</strong> (REST communication with <code>http://matiasborra.es:8081</code>)</li>
</ul>

<hr>

<h2 id="project-structure">📂 Project Structure</h2>
<pre><code>
src/main/java
├── com
│   └── matias
│       └── physiocarepsp
│           ├── MainApplication.java
│           ├── models
│           │   ├── Appointment
│           │   │   ├── AppointmentDto.java
│           │   │   ├── Appointment.java
│           │   │   ├── AppointmentListDto.java
│           │   │   ├── AppointmentListResponse.java
│           │   │   ├── AppointmentRequest.java
│           │   │   └── AppointmentResponse.java
│           │   ├── Auth
│           │   │   ├── AuthResponse.java
│           │   │   └── LoginRequest.java
│           │   ├── BaseResponse.java
│           │   ├── Patient
│           │   │   ├── Patient.java
│           │   │   ├── PatientListResponse.java
│           │   │   └── PatientResponse.java
│           │   ├── Physio
│           │   │   ├── Physio.java
│           │   │   ├── PhysioListResponse.java
│           │   │   └── PhysioResponse.java
│           │   └── Record
│           │       ├── Record.java
│           │       ├── RecordListResponse.java
│           │       └── RecordResponse.java
│           ├── utils
│           │   ├── AppointmentService.java
│           │   ├── EmailUtil.java
│           │   ├── LocalDateAdapter.java
│           │   ├── PDFUtil.java
│           │   ├── ServiceUtils.java
│           │   ├── SftpUploader.java
│           │   └── Utils.java
│           └── viewscontroller
│               ├── AppointmentsViewController.java
│               ├── CalendarController.java
│               ├── FirstViewController.java
│               ├── LoginViewController.java
│               ├── PatientsViewController.java
│               └── PhysiosViewController.java
└── module-info.java

</code></pre>

<hr>

<h2 id="installation">🎯 Installation</h2>
<ol>
  <li>
    <strong>Clone the repository</strong><br>
    <code>git clone https://github.com/pablogsf/PSP-PhysioCare.git</code><br>
    <code>cd PSP-PhysioCare/PhysioCarePSP-master</code>
  </li>
  <li>
    <strong>Ensure Java 23 is installed</strong> and on your <code>PATH</code>.
  </li>
  <li>
    <strong>Run the app</strong>:<br>
    <em>Linux/macOS:</em><br>
    <code>./mvnw clean javafx:run</code><br>
    <em>Windows:</em><br>
    <code>mvnw.cmd clean javafx:run</code>
  </li>
  <li>
    <strong>Login</strong> with your credentials to begin.
  </li>
</ol>

<hr>

<h2 id="contributing">🤝 Contributing</h2>
<ol>
  <li>Fork the repo</li>
  <li>Create a feature branch:<br><code>git checkout -b feature/awesome-feature</code></li>
  <li>Commit your changes</li>
  <li>Push to your fork &amp; open a Pull Request</li>
</ol>

<hr>

<h2 id="license">📄 License</h2>
<p>This project is licensed under the <strong>MIT License</strong>. See <a href="LICENSE">LICENSE</a> for details.</p>



🛠️ Qué falta por hacer

Flujo de subida de fichas

Un punto en UI (o un servicio en segundo plano) que recorra todos los Record (o los obtenga vía API), genere el PDF de cada ficha (sin incluir citas) y llame a SftpUploader.upload(host, port, user, pass, pdfBytes, pacienteId + ".pdf").

{{URL}}/records



Notificaciones por e-mail

Un NotificationService que:

Recoja todos los pacientes ({{URL}}/patients) y sus citas ({{URL}}/records/:id_patient/appointments).

Para cada uno con > 8 citas,({{URL}}/records/patient/:id_patient/appointments/count) genere el PDF con generateAppointmentsPdf(), y envíe un mail recordatorio con EmailUtil.send(…).

Recoja todos los fisioterapeutas ({{URL}}/physios) y sus citas ({{URL}}/records/physio/:physio_id/appointments), genere generateSalaryPdf(), y les envíe su nómina.


Integración UI/UX

Botones o menús para “Exportar fichas” y “Enviar notificaciones”. Falta programar el envío de correo al tener un patient 8 citas.

O bien programar estas tareas al arrancar la app.


Próximos pasos

Crear la clase NotificationService con toda la lógica de recopilación, generación de PDFs y envío SFTP/Email.

Añadir botones/vistas para disparar esos procesos manualmente. (“Exportar fichas” y “Enviar notificaciones”)
