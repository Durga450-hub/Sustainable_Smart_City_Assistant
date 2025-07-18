<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sustainable Smart City Assistant Using IBM Granite LLM</title>
    <style>
        @page {
            size: A4;
            margin: 20mm;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 210mm;
            margin: 0 auto;
            background: white;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
            min-height: 100vh;
        }
        
        .header {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><circle cx="20" cy="20" r="2" fill="rgba(255,255,255,0.1)"/><circle cx="80" cy="40" r="3" fill="rgba(255,255,255,0.1)"/><circle cx="40" cy="80" r="1" fill="rgba(255,255,255,0.1)"/><circle cx="90" cy="90" r="2" fill="rgba(255,255,255,0.1)"/></svg>');
            animation: float 20s infinite linear;
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .project-title {
            font-size: 2.5em;
            font-weight: bold;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            position: relative;
            z-index: 1;
        }
        
        .content {
            padding: 40px;
        }
        
        .section {
            margin-bottom: 40px;
            page-break-inside: avoid;
        }
        
        .section-title {
            font-size: 1.8em;
            color: #4CAF50;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 3px solid #4CAF50;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .phase-title {
            font-size: 1.4em;
            color: #2196F3;
            margin: 25px 0 15px 0;
            padding: 10px 15px;
            background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%);
            border-left: 4px solid #2196F3;
            border-radius: 5px;
        }
        
        .team-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-top: 20px;
        }
        
        .team-member {
            background: linear-gradient(135deg, #f5f5f5 0%, #e8e8e8 100%);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }
        
        .team-member:hover {
            transform: translateY(-5px);
        }
        
        .team-member.leader {
            background: linear-gradient(135deg, #fff3e0 0%, #ffcc02 100%);
            border: 2px solid #ff9800;
        }
        
        .objective-box {
            background: linear-gradient(135deg, #e8f5e8 0%, #c8e6c9 100%);
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid #4CAF50;
            margin: 20px 0;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        
        .problem-box {
            background: linear-gradient(135deg, #fff3e0 0%, #ffe0b2 100%);
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid #ff9800;
            margin: 20px 0;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        
        .diagram-container {
            background: #f8f9fa;
            border: 2px dashed #ddd;
            border-radius: 10px;
            padding: 40px;
            margin: 20px 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .diagram-placeholder {
            color: #666;
            font-size: 1.1em;
            margin-bottom: 20px;
        }
        
        .diagram-visual {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2em;
            font-weight: bold;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
            position: relative;
        }
        
        .smart-city-diagram {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            position: relative;
        }
        
        .smart-city-diagram::before {
            content: '🏙️ 🌱 🚗 🗑️ 🌡️';
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2em;
            opacity: 0.3;
        }
        
        .cnn-diagram {
            background: linear-gradient(135deg, #2196F3 0%, #1976D2 100%);
            position: relative;
        }
        
        .cnn-diagram::before {
            content: '🧠 → 📊 → 🎯';
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2.5em;
            opacity: 0.3;
        }
        
        .llm-diagram {
            background: linear-gradient(135deg, #9C27B0 0%, #7B1FA2 100%);
            position: relative;
        }
        
        .llm-diagram::before {
            content: '🤖 + 🖼️ = 💡';
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2.5em;
            opacity: 0.3;
        }
        
        .ui-mockup {
            background: linear-gradient(135deg, #FF5722 0%, #D84315 100%);
            position: relative;
        }
        
        .ui-mockup::before {
            content: '📱 💻 🖥️';
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 2.5em;
            opacity: 0.3;
        }
        
        .phase-list {
            list-style: none;
            padding-left: 0;
        }
        
        .phase-list li {
            background: #f8f9fa;
            margin: 10px 0;
            padding: 15px;
            border-radius: 8px;
            border-left: 4px solid #4CAF50;
            position: relative;
            transition: all 0.3s ease;
        }
        
        .phase-list li:hover {
            background: #e8f5e8;
            transform: translateX(5px);
        }
        
        .phase-list li::before {
            content: '✓';
            position: absolute;
            left: -15px;
            top: 50%;
            transform: translateY(-50%);
            background: #4CAF50;
            color: white;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 0.9em;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-top: 20px;
        }
        
        .feature-card {
            background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .feature-card h4 {
            color: #1976D2;
            margin-bottom: 10px;
        }
        
        .emoji {
            font-size: 1.5em;
            margin-right: 10px;
        }
        
        .footer {
            background: #333;
            color: white;
            padding: 20px;
            text-align: center;
            margin-top: 40px;
        }
        
        @media print {
            .container {
                box-shadow: none;
                max-width: 100%;
            }
            
            .header::before {
                animation: none;
            }
            
            .team-member:hover,
            .phase-list li:hover {
                transform: none;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1 class="project-title">🌟 Sustainable Smart City Assistant Using IBM Granite LLM</h1>
            <p style="font-size: 1.2em; margin-top: 10px;">Advanced AI Solution for Urban Sustainability</p>
        </div>
        
        <div class="content">
            <div class="section">
                <h2 class="section-title">
                    <span class="emoji">👥</span>
                    Team Members
                </h2>
                <div class="team-grid">
                    <div class="team-member leader">
                        <h3>Y. Durgeswari</h3>
                        <p><strong>Team Leader</strong></p>
                        <p>👑 Project Management & Strategy</p>
                    </div>
                    <div class="team-member">
                        <h3>Pb Sujitha</h3>
                        <p>🧠 AI/ML Development</p>
                    </div>
                    <div class="team-member">
                        <h3>M. Sravani</h3>
                        <p>🎨 Frontend Development</p>
                    </div>
                    <div class="team-member">
                        <h3>P. Pavan Kumar</h3>
                        <p>⚙️ Backend Integration</p>
                    </div>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">
                    <span class="emoji">🔍</span>
                    Problem Statement
                </h2>
                <div class="problem-box">
                    <p>Managing a growing smart city demands real-time insights from diverse data sources like images, weather feeds, surveillance, and infrastructure systems. Traditional systems lack the AI capability to process this unstructured data for sustainable urban planning.</p>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">
                    <span class="emoji">🎯</span>
                    Objective
                </h2>
                <div class="objective-box">
                    <p>To build a machine learning-based assistant that uses CNN models for image analysis and IBM Granite LLM to assist in real-time decision-making, with a user interface built using Streamlit and a visually appealing frontend.</p>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">
                    <span class="emoji">🧩</span>
                    Project Development Phases
                </h2>
                
                <div class="phase-title">📌 Phase 1: Problem Understanding & Dataset Collection</div>
                <ul class="phase-list">
                    <li>Identify key features needed for a smart city assistant</li>
                    <li>Collect image data related to traffic, waste, pollution, green cover</li>
                    <li>Gather weather and environmental data</li>
                </ul>
                
                <div class="diagram-container">
                    <div class="diagram-placeholder">Smart City Image Dataset Overview</div>
                    <div class="diagram-visual smart-city-diagram">
                        <div>
                            <h3>Smart City Data Sources</h3>
                            <p>Traffic • Waste Management • Pollution Monitoring • Green Cover Analysis</p>
                        </div>
                    </div>
                </div>
                
                <div class="phase-title">📌 Phase 2: Image Processing with CNN</div>
                <ul class="phase-list">
                    <li>Develop and train CNN models using Python (TensorFlow/Keras)</li>
                    <li>Focus on classification and detection tasks</li>
                    <li>Validate the models using test datasets</li>
                </ul>
                
                <div class="diagram-container">
                    <div class="diagram-placeholder">CNN Model Training Pipeline</div>
                    <div class="diagram-visual cnn-diagram">
                        <div>
                            <h3>CNN Training Pipeline</h3>
                            <p>Data Preprocessing → Model Training → Validation → Deployment</p>
                        </div>
                    </div>
                </div>
                
                <div class="phase-title">📌 Phase 3: Integration of IBM Granite LLM</div>
                <ul class="phase-list">
                    <li>Use IBM's foundation model to generate intelligent insights</li>
                    <li>Perform natural language understanding on user queries</li>
                    <li>Create smart suggestions for traffic rerouting, waste management, etc.</li>
                </ul>
                
                <div class="diagram-container">
                    <div class="diagram-placeholder">LLM + CNN Integration Flow</div>
                    <div class="diagram-visual llm-diagram">
                        <div>
                            <h3>AI Integration Architecture</h3>
                            <p>CNN Image Analysis + IBM Granite LLM = Smart City Insights</p>
                        </div>
                    </div>
                </div>
                
                <div class="phase-title">📌 Phase 4: Streamlit Deployment & Frontend Development</div>
                <ul class="phase-list">
                    <li>Build a clean user interface with HTML + CSS embedded in Streamlit</li>
                    <li>Deploy functionalities: Upload image, View AI classification, Get LLM-based suggestions</li>
                    <li>Dashboard for sustainability metrics</li>
                </ul>
                
                <div class="features-grid">
                    <div class="feature-card">
                        <h4>📤 Image Upload</h4>
                        <p>Easy drag-and-drop interface for image analysis</p>
                    </div>
                    <div class="feature-card">
                        <h4>🔍 AI Classification</h4>
                        <p>Real-time image classification results</p>
                    </div>
                    <div class="feature-card">
                        <h4>💡 Smart Suggestions</h4>
                        <p>LLM-powered recommendations</p>
                    </div>
                    <div class="feature-card">
                        <h4>📊 Sustainability Dashboard</h4>
                        <p>Comprehensive metrics and analytics</p>
                    </div>
                </div>
                
                <div class="diagram-container">
                    <div class="diagram-placeholder">UI Screenshot Preview</div>
                    <div class="diagram-visual ui-mockup">
                        <div>
                            <h3>Streamlit User Interface</h3>
                            <p>Interactive Dashboard with AI-Powered Features</p>
                        </div>
                    </div>
                </div>
                
                <div class="phase-title">📌 Phase 5: Final Deployment & Testing</div>
                <ul class="phase-list">
                    <li>Deploy the application to the cloud (optional: Hugging Face or Streamlit Cloud)</li>
                    <li>Conduct testing with different inputs and real-time simulation</li>
                    <li>Collect user feedback and optimize</li>
                </ul>
            </div>
        </div>
        
        <div class="footer">
            <p><strong>Sustainable Smart City Assistant Project</strong></p>
            <p>Leveraging IBM Granite LLM and CNN for Urban Intelligence</p>
            <p>© 2025 - Team Durgeswari</p>
        </div>
    </div>
    
    <script>
        // Add print functionality
        document.addEventListener('keydown', function(e) {
            if (e.ctrlKey && e.key === 'p') {
                window.print();
                e.preventDefault();
            }
        });
        
        // Add smooth scrolling for better UX
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>