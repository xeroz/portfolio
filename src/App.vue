<script setup lang="ts">
import { ref } from 'vue'

interface Project {
  title: string
  subtitle: string
  challenge: string
  solution: string
  technologies: string[]
}

const name = ref('Juan Chávez Vásquez')
const role = ref('Software Developer')
const location = ref('Lima, Perú')
const email = ref('chavezvasquezjuan@gmail.com')
const phone = ref('992850243')

const skills = ref([
  { name: 'python', level: 'Experimentado/a' },
  { name: 'php', level: 'Cualificado/a' },
  { name: '.net', level: 'Cualificado/a' },
  { name: 'Linux', level: 'Cualificado/a' }
])

const projects = ref<Project[]>([
  {
    title: 'Simulador de Bolsa de Valores en Entorno Web',
    subtitle: 'NorthSouth Studios Peru | Cliente: Junior Achievement (2021 - 2026)',
    challenge: 'Renderizar fluctuaciones del mercado financiero en vivo sin demoras de recarga y estructurar un backend sólido para transacciones concurrentes.',
    solution: 'Desarrollo de frontend con Vue.js y uso de WebSockets para el manejo de data en tiempo real. Implementación del backend con .NET y optimización de consultas/procedimientos almacenados mediante SQL Server.',
    technologies: ['Vue.js', '.NET', 'WebSockets', 'SQL Server']
  },
  {
    title: 'Vocana – App Mobile de Música por Streaming',
    subtitle: 'NorthSouth Studios Peru (2021 - 2026)',
    challenge: 'Manejar eficientemente grandes volúmenes de datos multimedia, gestionar pagos internacionales recurrentes y garantizar la velocidad de respuesta del servidor.',
    solution: 'Desarrollo de APIs utilizando Django (Python), integración de pasarela de pagos con Stripe y modelamiento de bases de datos relacionales en Postgres. Análisis de rendimiento en servidores con AWS.',
    technologies: ['Python', 'Django', 'PostgreSQL', 'Stripe', 'AWS']
  },
  {
    title: 'Pipelines ETL & Arquitectura Serverless',
    subtitle: 'Celer SAC - Outsourcing (2019 - 2020)',
    challenge: 'Procesar flujos de datos masivos de manera eficiente sin incurrir en costos fijos elevados de servidores encendidos 24/7.',
    solution: 'Desarrollo de aplicativos ETL en Python usando AWS Glue y AWS Batch. Diseño de APIs usando Serverless para AWS Lambda, configuración de Docker en AWS EC2 e implementación de integración continua (CI/CD) con GitLab Server.',
    technologies: ['Python', 'AWS Lambda', 'AWS Glue', 'AWS Batch', 'Docker', 'CI/CD', 'GitLab']
  },
  {
    title: 'Sistema de Agendamiento de Citas Médicas',
    subtitle: 'Continuum | Cliente: MINSAL Chile (2019 - 2020)',
    challenge: 'Desarrollar una plataforma altamente confiable bajo estándares gubernamentales estrictos, garantizando que los despliegues no introdujeran errores.',
    solution: 'Implementación del backend y frontend de acuerdo a los requerimientos del cliente y desarrollo exhaustivo de pruebas unitarias para asegurar la estabilidad del sistema.',
    technologies: ['Frontend', 'Backend', 'Unit Testing']
  }
])
</script>

<template>
  <div class="portfolio-container">
    <div class="portfolio-card">

      <!-- COLUMNA PRINCIPAL (Izquierda): Experiencia y Proyectos -->
      <main class="main-content">
        <header class="header-section">
          <h1 class="candidate-name">{{ name }}</h1>
          <p class="candidate-role">{{ role }}</p>
        </header>

        <section class="section">
          <h2 class="section-title">Experiencia Laboral & Casos de Éxito</h2>
          <div class="projects-list">
            <article v-for="(project, index) in projects" :key="index" class="project-item">
              <h3 class="project-title">{{ project.title }}</h3>
              <p class="project-subtitle">{{ project.subtitle }}</p>

              <div class="project-details">
                <p><strong>El Reto:</strong> {{ project.challenge }}</p>
                <p><strong>Solución técnica:</strong> {{ project.solution }}</p>
              </div>

              <div class="tech-tags">
                <span v-for="tech in project.technologies" :key="tech" class="tag">
                  {{ tech }}
                </span>
              </div>
            </article>
          </div>
        </section>

        <section class="section">
          <h2 class="section-title">Educación</h2>
          <div class="education-item">
            <h3>Universidad Nacional Mayor de San Marcos, Lima</h3>
            <p class="education-status">Estudiante Egresado</p>
          </div>
        </section>
      </main>

      <!-- COLUMNA LATERAL (Derecha): Datos de contacto y Competencias -->
      <aside class="sidebar">
        <section class="sidebar-section">
          <h2 class="sidebar-title">Detalles</h2>
          <p class="sidebar-text">📍 {{ location }}</p>
          <p class="sidebar-text">📞 {{ phone }}</p>
          <p class="sidebar-text">
            ✉️ <a :href="'mailto:' + email" class="sidebar-link">{{ email }}</a>
          </p>
          <p class="sidebar-text"><strong>Nacionalidad:</strong> Peruano</p>
        </section>

        <section class="sidebar-section">
          <h2 class="sidebar-title">Perfiles Sociales</h2>
          <p class="sidebar-text"><a href="#" target="_blank" class="sidebar-link">🚀 LinkedIn</a></p>
          <p class="sidebar-text"><a href="#" target="_blank" class="sidebar-link">🛠️ GitHub</a></p>
        </section>

        <section class="sidebar-section">
          <h2 class="sidebar-title">Competencias</h2>
          <div class="skill-item" v-for="skill in skills" :key="skill.name">
            <span class="skill-name">{{ skill.name }}</span>
            <span class="skill-level">{{ skill.level }}</span>
          </div>
        </section>

        <section class="sidebar-section">
          <h2 class="sidebar-title">Idiomas</h2>
          <p class="sidebar-text"><strong>Español:</strong> Nativo</p>
          <p class="sidebar-text"><strong>Inglés:</strong> A1</p>
        </section>

        <section class="sidebar-section">
          <h2 class="sidebar-title">Hobbies</h2>
          <p class="sidebar-text text-justify">Programo por un simple gusto y por crecimiento profesional. Me gusta la natación.</p>
        </section>
      </aside>

    </div>
  </div>
</template>

<style scoped>
/* --- ESTILOS CSS PUROS (Formato Estilo PDF Ejecutivo) --- */

.portfolio-container {
  background-color: #f4f6f9;
  min-height: 100vh;
  padding: 40px 20px;
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  color: #333333;
  display: flex;
  justify-content: center;
}

.portfolio-card {
  background: #ffffff;
  max-width: 1000px;
  width: 100%;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  display: grid;
  grid-template-columns: 2fr 1fr;
  border-radius: 4px;
  overflow: hidden;
}

/* Columna Principal */
.main-content {
  padding: 40px;
  border-right: 1px solid #eef2f5;
}

.header-section {
  border-bottom: 2px solid #2c3e50;
  padding-bottom: 20px;
  margin-bottom: 30px;
}

.candidate-name {
  font-size: 32px;
  font-weight: 700;
  color: #1a252f;
  margin: 0 0 5px 0;
}

.candidate-role {
  font-size: 18px;
  color: #7f8c8d;
  margin: 0;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.section {
  margin-bottom: 35px;
}

.section-title {
  font-size: 18px;
  color: #2c3e50;
  border-bottom: 1px solid #bdc3c7;
  padding-bottom: 6px;
  margin-bottom: 20px;
  text-transform: uppercase;
}

.projects-list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.project-item {
  border-bottom: 1px dashed #e2e8f0;
  padding-bottom: 20px;
}

.project-item:last-child {
  border-bottom: none;
  padding-bottom: 0;
}

.project-title {
  font-size: 16px;
  color: #2c3e50;
  margin: 0 0 4px 0;
  font-weight: 600;
}

.project-subtitle {
  font-size: 13px;
  color: #16a085;
  margin: 0 0 12px 0;
  font-style: italic;
}

.project-details p {
  font-size: 13.5px;
  line-height: 1.5;
  margin: 0 0 8px 0;
  color: #4a5568;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 12px;
}

.tag {
  background-color: #ebf8ff;
  color: #2b6cb0;
  font-size: 11px;
  padding: 3px 8px;
  border-radius: 3px;
  font-weight: 500;
  border: 1px solid #bee3f8;
}

.education-item h3 {
  font-size: 15px;
  margin: 0 0 4px 0;
  color: #2c3e50;
}

.education-status {
  font-size: 13px;
  color: #7f8c8d;
  margin: 0;
}

/* Columna Lateral (Sidebar) */
.sidebar {
  background-color: #f8fafc;
  padding: 40px 30px;
}

.sidebar-section {
  margin-bottom: 30px;
}

.sidebar-title {
  font-size: 14px;
  color: #2c3e50;
  border-bottom: 1px solid #cbd5e1;
  padding-bottom: 4px;
  margin-bottom: 12px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.sidebar-text {
  font-size: 13px;
  line-height: 1.5;
  margin: 0 0 8px 0;
  color: #475569;
}

.text-justify {
  text-align: justify;
}

.sidebar-link {
  color: #2b6cb0;
  text-decoration: none;
}

.sidebar-link:hover {
  text-decoration: underline;
}

.skill-item {
  display: flex;
  justify-content: space-between;
  font-size: 13px;
  margin-bottom: 6px;
  padding-bottom: 4px;
  border-bottom: 1px solid #f1f5f9;
}

.skill-name {
  font-weight: 600;
  color: #334155;
}

.skill-level {
  color: #64748b;
}

/* Responsivo para móviles */
@media (max-width: 768px) {
  .portfolio-card {
    grid-template-columns: 1fr;
  }
  .main-content {
    border-right: none;
    border-bottom: 1px solid #eef2f5;
    padding: 30px 20px;
  }
  .sidebar {
    padding: 30px 20px;
  }
}
</style>