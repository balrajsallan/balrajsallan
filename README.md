<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Balraj Sallan · Software Developer</title>
    <!-- Chart.js & Font Awesome CDN -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
    <style>
        /* === Reset & Base === */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #181818;
            font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'SF Pro Text', 'Helvetica Neue', Helvetica, Arial, sans-serif;
            color: #ffffff;
            padding: 2rem 1.5rem;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        /* === Typography === */
        h1, h2, h3, h4 {
            font-weight: 600;
            letter-spacing: -0.02em;
        }

        .subtitle {
            color: #818589;
            font-size: 1.1rem;
            margin-top: 0.25rem;
        }

        .section-title {
            font-size: 1.8rem;
            margin: 2.5rem 0 1.5rem;
            border-bottom: 1px solid #333;
            padding-bottom: 0.5rem;
            display: inline-block;
        }

        /* === Header === */
        .header {
            text-align: center;
            margin-bottom: 2.5rem;
        }

        .header h1 {
            font-size: 3rem;
            color: #ffffff;
            margin-bottom: 0.2rem;
        }

        .header .subtitle {
            font-size: 1.2rem;
        }

        .bio {
            max-width: 800px;
            margin: 1.5rem auto 0;
            color: #cccccc;
            font-size: 1rem;
            line-height: 1.7;
        }

        .bio strong {
            color: #ffffff;
        }

        /* === Contribution Graph === */
        .graph-wrapper {
            margin: 2rem 0;
            background: #1e1e1e;
            border-radius: 12px;
            padding: 0.5rem;
            box-shadow: 0 8px 24px rgba(0,0,0,0.4);
        }

        .graph-wrapper img {
            display: block;
            width: 100%;
            height: auto;
            border-radius: 8px;
        }

        /* === Two‑column layout for charts === */
        .charts-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin: 2.5rem 0;
        }

        .chart-card {
            background: #1e1e1e;
            border-radius: 12px;
            padding: 1.5rem 1rem 1rem;
            box-shadow: 0 4px 16px rgba(0,0,0,0.3);
        }

        .chart-card h3 {
            text-align: center;
            color: #cccccc;
            font-weight: 400;
            font-size: 1.1rem;
            margin-bottom: 1rem;
            letter-spacing: 0.5px;
        }

        .chart-card canvas {
            max-height: 280px;
            max-width: 100%;
            margin: 0 auto;
            display: block;
        }

        /* === Project Showcase === */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin: 2rem 0 3rem;
        }

        .project-card {
            background: #1e1e1e;
            border-radius: 12px;
            padding: 1.8rem 1.5rem;
            transition: transform 0.25s ease, box-shadow 0.25s ease;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
            border: 1px solid #2a2a2a;
        }

        .project-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 12px 32px rgba(0,0,0,0.5);
        }

        .project-card .icon {
            font-size: 2.2rem;
            color: #ffffff;
            margin-bottom: 0.75rem;
        }

        .project-card h3 {
            font-size: 1.4rem;
            color: #ffffff;
            margin-bottom: 0.4rem;
        }

        .project-card .desc {
            color: #aaaaaa;
            font-size: 0.95rem;
            margin: 0.5rem 0 1rem;
            line-height: 1.5;
        }

        .project-card .stack {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .project-card .stack span {
            background: #2a2a2a;
            color: #dddddd;
            padding: 0.2rem 0.7rem;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 500;
            letter-spacing: 0.3px;
        }

        .project-card .link {
            display: inline-block;
            margin-top: 1rem;
            color: #aaaaaa;
            text-decoration: none;
            font-weight: 500;
            border-bottom: 1px solid transparent;
            transition: border-color 0.2s;
        }

        .project-card .link:hover {
            border-color: #ffffff;
            color: #ffffff;
        }

        /* === Social Badges === */
        .social-section {
            text-align: center;
            margin: 3rem 0 2rem;
        }

        .social-section .badges {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 0.6rem;
            margin-top: 1rem;
        }

        .social-section .badges a {
            display: inline-block;
            background: #181818;
            padding: 0.5rem 1.2rem;
            border-radius: 30px;
            color: #ffffff;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            border: 1px solid #333;
            transition: background 0.2s, border-color 0.2s;
        }

        .social-section .badges a:hover {
            background: #2a2a2a;
            border-color: #555;
        }

        .social-section .badges a i {
            margin-right: 0.5rem;
            width: 1.2em;
            text-align: center;
        }

        /* === Footer === */
        .footer {
            text-align: center;
            color: #888888;
            font-size: 0.85rem;
            margin-top: 3rem;
            border-top: 1px solid #2a2a2a;
            padding-top: 2rem;
        }

        .footer b {
            color: #aaaaaa;
        }

        /* === Responsive === */
        @media (max-width: 768px) {
            .charts-row {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .header h1 {
                font-size: 2.4rem;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .bio {
                font-size: 0.95rem;
            }
        }

        /* small tweaks */
        .badge-matte {
            background: #181818;
            color: #fff;
            border: 1px solid #333;
        }
    </style>
</head>
<body>

<div class="container">

    <!-- ========== HEADER ========== -->
    <header class="header">
        <h1>Software Developer</h1>
        <p class="subtitle">Full-Stack &amp; Cloud Architect · Crafting Digital Experiences</p>
        <div class="bio">
            <strong>Balraj Sallan</strong> is an innovative Software Developer dedicated to engineering elegant, scalable, and user‑centric digital experiences. Possessing a versatile technical arsenal—spanning core web technologies like HTML5, CSS3, and JavaScript, to high‑performance languages and frameworks like Python, Swift, Node.js, and Three.js—Balraj seamlessly bridges creative front‑end aesthetics with robust backend systems. Beyond web and mobile development, his expertise in modern DevOps tools like Docker and Kubernetes reflects a strong commitment to cloud‑native practices, deployment automation, and system reliability.
        </div>
    </header>

    <!-- ========== CONTRIBUTION GRAPH ========== -->
    <div class="graph-wrapper">
        <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=balrajsallan&theme=dark" alt="Contribution Graph" />
    </div>

    <!-- ========== CHARTS ROW ========== -->
    <div class="charts-row">

        <!-- Radar Chart: Skills -->
        <div class="chart-card">
            <h3><i class="fas fa-bolt" style="margin-right: 8px; color: #818589;"></i> Skill Proficiency</h3>
            <canvas id="radarChart" width="400" height="300"></canvas>
        </div>

        <!-- Bar Chart: Project Metrics -->
        <div class="chart-card">
            <h3><i class="fas fa-chart-bar" style="margin-right: 8px; color: #818589;"></i> Project Activity</h3>
            <canvas id="barChart" width="400" height="300"></canvas>
        </div>

    </div>

    <!-- ========== PROJECT SHOWCASE ========== -->
    <h2 class="section-title">Featured Projects</h2>
    <div class="projects-grid">

        <!-- Project 1 -->
        <div class="project-card">
            <div class="icon"><i class="fas fa-brain"></i></div>
            <h3>Inteligence</h3>
            <div class="desc">
                Forward‑thinking platform blending modern aesthetics with next‑gen computation and interactive 3D graphics.
            </div>
            <div class="stack">
                <span>Three.js</span>
                <span>Node.js</span>
                <span>WebGL</span>
            </div>
            <a href="#" class="link">Explore Project →</a>
        </div>

        <!-- Project 2 -->
        <div class="project-card">
            <div class="icon"><i class="fas fa-check-circle"></i></div>
            <h3>Habit Tracker</h3>
            <div class="desc">
                Sleek productivity app for building daily consistency with streak visualizers and client‑side state management.
            </div>
            <div class="stack">
                <span>HTML5</span>
                <span>CSS3</span>
                <span>JavaScript</span>
            </div>
            <a href="#" class="link">Explore Project →</a>
        </div>

        <!-- Project 3 -->
        <div class="project-card">
            <div class="icon"><i class="fas fa-gamepad"></i></div>
            <h3>Tic Tac Toe</h3>
            <div class="desc">
                Interactive strategy game featuring dynamic turn mechanics, win detection, and minimalist animations.
            </div>
            <div class="stack">
                <span>JavaScript</span>
                <span>DOM</span>
                <span>CSS3</span>
            </div>
            <a href="#" class="link">Explore Project →</a>
        </div>

    </div>

    <!-- ========== SOCIAL ========== -->
    <div class="social-section">
        <h3 style="color: #cccccc; font-weight: 400; margin-bottom: 0.5rem;">Connect &amp; Network</h3>
        <div class="badges">
            <a href="https://youtube.com/@balrajsallani"><i class="fab fa-youtube"></i> YouTube</a>
            <a href="https://www.linkedin.com/in/balraj-sallan-a22724426"><i class="fab fa-linkedin-in"></i> LinkedIn</a>
            <a href="https://www.instagram.com/dimes.labs"><i class="fab fa-instagram"></i> Instagram</a>
            <a href="https://www.facebook.com/profile.php?id=61551654367713"><i class="fab fa-facebook-f"></i> Facebook</a>
        </div>
    </div>

    <!-- ========== FOOTER ========== -->
    <div class="footer">
        Designed &amp; Engineered with precision for <b>@balrajsallan</b>
    </div>

</div>

<!-- ========== CHARTS SCRIPT ========== -->
<script>
    document.addEventListener('DOMContentLoaded', function () {

        // -------- RADAR CHART (Skills) --------
        const ctxRadar = document.getElementById('radarChart').getContext('2d');

        new Chart(ctxRadar, {
            type: 'radar',
            data: {
                labels: ['HTML/CSS/JS', 'Python', 'Swift', 'Node.js', 'Three.js', 'Docker/K8s', 'Flutter'],
                datasets: [{
                    label: 'Proficiency',
                    data: [95, 88, 75, 82, 78, 85, 70],
                    backgroundColor: 'rgba(255, 255, 255, 0.08)',
                    borderColor: '#ffffff',
                    borderWidth: 2,
                    pointBackgroundColor: '#ffffff',
                    pointBorderColor: '#181818',
                    pointRadius: 4,
                    pointHoverRadius: 6,
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: true,
                plugins: {
                    legend: {
                        display: false, // we already have a title
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                return context.raw + '%';
                            }
                        }
                    }
                },
                scales: {
                    r: {
                        angleLines: { color: '#333333' },
                        grid: { color: '#2a2a2a' },
                        pointLabels: {
                            color: '#cccccc',
                            font: { size: 11, family: "'SF Pro Display', sans-serif" }
                        },
                        ticks: {
                            backdropColor: 'transparent',
                            color: '#aaaaaa',
                            stepSize: 20,
                            display: false // hide numeric labels for cleaner look
                        },
                        suggestedMin: 0,
                        suggestedMax: 100,
                    }
                }
            }
        });

        // -------- BAR CHART (Project Stats) --------
        const ctxBar = document.getElementById('barChart').getContext('2d');

        new Chart(ctxBar, {
            type: 'bar',
            data: {
                labels: ['Inteligence', 'Habit Tracker', 'Tic Tac Toe'],
                datasets: [
                    {
                        label: 'Commits',
                        data: [42, 28, 15],
                        backgroundColor: '#4a4a4a',
                        borderRadius: 4,
                    },
                    {
                        label: 'Issues Closed',
                        data: [12, 8, 5],
                        backgroundColor: '#6a6a6a',
                        borderRadius: 4,
                    },
                    {
                        label: '⭐ Stars',
                        data: [7, 12, 3],
                        backgroundColor: '#8a8a8a',
                        borderRadius: 4,
                    }
                ]
            },
            options: {
                responsive: true,
                maintainAspectRatio: true,
                plugins: {
                    legend: {
                        labels: {
                            color: '#cccccc',
                            font: { size: 11, family: "'SF Pro Display', sans-serif" },
                            boxWidth: 12,
                            padding: 15,
                        }
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                return context.dataset.label + ': ' + context.raw;
                            }
                        }
                    }
                },
                scales: {
                    x: {
                        grid: { color: '#2a2a2a' },
                        ticks: { color: '#cccccc', font: { size: 11 } }
                    },
                    y: {
                        grid: { color: '#2a2a2a' },
                        ticks: { color: '#aaaaaa', stepSize: 5, font: { size: 10 } },
                        beginAtZero: true,
                    }
                }
            }
        });

    });
</script>

</body>
</html>
