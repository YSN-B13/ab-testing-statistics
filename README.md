<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A/B Testing Analysis</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-mml-chtml.min.js"></script>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.8;
            max-width: 900px;
            margin: 0 auto;
            padding: 40px 20px;
            background: #f5f5f5;
            color: #333;
        }
        h1 {
            color: #2c3e50;
            border-bottom: 3px solid #3498db;
            padding-bottom: 10px;
        }
        h2 {
            color: #34495e;
            margin-top: 30px;
        }
        h3 {
            color: #7f8c8d;
        }
        .equation-block {
            background: white;
            padding: 20px;
            margin: 20px 0;
            border-left: 4px solid #3498db;
            border-radius: 4px;
            overflow-x: auto;
        }
        .note {
            background: #fff3cd;
            padding: 15px;
            border-left: 4px solid #ffc107;
            margin: 15px 0;
            border-radius: 4px;
        }
        .decision {
            background: #d4edda;
            padding: 15px;
            border-left: 4px solid #28a745;
            margin: 15px 0;
            border-radius: 4px;
        }
        p {
            margin: 12px 0;
        }
        ul {
            margin: 12px 0;
            padding-left: 20px;
        }
        li {
            margin: 8px 0;
        }
    </style>
</head>
<body>
    <h1>🧪 A/B Testing Analysis</h1>
    
    <h2>📘 Overview</h2>
    <p>This guide presents a comprehensive A/B testing analysis to determine whether an experimental change produces a statistically significant improvement over a control group.</p>
    
    <h2>🎯 Goal</h2>
    <p><strong>Does the experiment meaningfully improve conversion or click-through rates compared to control?</strong></p>
    
    <hr>
    
    <h2>📈 Methodology</h2>
    
    <h3>1. Hypothesis Definition</h3>
    <p>We test:</p>
    <div class="equation-block">
        $$H_0: P_{\text{control}} = P_{\text{experiment}} \quad \text{vs} \quad H_1: P_{\text{control}} \neq P_{\text{experiment}}$$
    </div>
    <p>where \(P_{\text{control}}\) and \(P_{\text{experiment}}\) are the true conversion rates for control and experiment.</p>
    
    <h3>2. Parameter Definitions</h3>
    <ul>
        <li>\(\alpha\): Significance level (Type I error rate)</li>
        <li>\(\beta\): Probability of Type II error</li>
        <li>\(1 - \beta\): Statistical power</li>
        <li>\(\delta\): Minimum detectable effect (MDE)</li>
    </ul>
    
    <h3>3. Proportion Estimates</h3>
    <p>Observed (sample) proportions:</p>
    <div class="equation-block">
        $$\hat{p}_{\text{control}} = \frac{\text{clicks}_{\text{control}}}{\text{impressions}_{\text{control}}}, \quad \hat{p}_{\text{experiment}} = \frac{\text{clicks}_{\text{experiment}}}{\text{impressions}_{\text{experiment}}}$$
    </div>
    <p>Sample sizes:</p>
    <div class="equation-block">
        $$n_{\text{control}} = \text{impressions}_{\text{control}}, \quad n_{\text{experiment}} = \text{impressions}_{\text{experiment}}$$
    </div>
    
    <h3>4. Pooled Proportion and Standard Error</h3>
    <p>When the null hypothesis assumes equal proportions, use the pooled estimate:</p>
    <div class="equation-block">
        $$\hat{p}_{\text{pooled}} = \frac{\text{clicks}_{\text{control}} + \text{clicks}_{\text{experiment}}}{n_{\text{control}} + n_{\text{experiment}}}$$
    </div>
    <p>Pooled standard error for the difference in proportions:</p>
    <div class="equation-block">
        $$SE_{\text{pooled}} = \sqrt{\hat{p}_{\text{pooled}}(1 - \hat{p}_{\text{pooled}})\left(\frac{1}{n_{\text{control}}} + \frac{1}{n_{\text{experiment}}}\right)}$$
    </div>
    <p class="note"><strong>Note:</strong> For confidence intervals, use the unpooled standard error:</p>
    <div class="equation-block">
        $$SE_{\text{unpooled}} = \sqrt{\frac{\hat{p}_{\text{control}}(1 - \hat{p}_{\text{control}})}{n_{\text{control}}} + \frac{\hat{p}_{\text{experiment}}(1 - \hat{p}_{\text{experiment}})}{n_{\text{experiment}}}}$$
    </div>
    
    <h3>5. Z-Test and P-value</h3>
    <p>Z-statistic (two-sample z-test):</p>
    <div class="equation-block">
        $$z = \frac{\hat{p}_{\text{experiment}} - \hat{p}_{\text{control}}}{SE_{\text{pooled}}}$$
    </div>
    <p>Two-sided p-value:</p>
    <div class="equation-block">
        $$p\text{-value} = 2 \times \big(1 - \Phi(|z|)\big)$$
    </div>
    <p>where \(\Phi\) is the standard normal CDF. Compare \(p\) to \(\alpha\) (commonly 0.05).</p>
    
    <h3>6. Confidence Interval for Difference</h3>
    <p>A \((1 - \alpha)\) two-sided confidence interval for \(\hat{p}_{\text{experiment}} - \hat{p}_{\text{control}}\) uses the unpooled SE:</p>
    <div class="equation-block">
        $$(\hat{p}_{\text{experiment}} - \hat{p}_{\text{control}}) \pm z_{1-\alpha/2} \cdot SE_{\text{unpooled}}$$
    </div>
    <p>where \(z_{1-\alpha/2}\) is the standard normal critical value (e.g., 1.96 for 95% CI).</p>
    
    <h3>7. Decision Rule & Interpretation</h3>
    <div class="decision">
        <ul>
            <li>If \(p < \alpha\): reject \(H_0\) → <strong>significant difference detected</strong></li>
            <li>If \(p \geq \alpha\): fail to reject \(H_0\) → <strong>no significant difference</strong></li>
        </ul>
        <p>If the confidence interval <strong>does not contain 0</strong>, this supports a significant difference at the chosen confidence level.</p>
    </div>
    
    <h3>8. Practical Notes</h3>
    <ul>
        <li>Use pooled SE for the hypothesis test only when \(H_0\) assumes equal proportions and sample sizes are large</li>
        <li>Use unpooled SE for confidence intervals and when variance differs between groups</li>
        <li>For small samples or extreme proportions, consider exact tests (Fisher's exact test) or continuity corrections</li>
    </ul>
    
    <h2>📊 Results Summary</h2>
    <p>The analysis outputs:</p>
    <ul>
        <li>Conversion rate comparison: \(\hat{p}_{\text{control}}\) vs \(\hat{p}_{\text{experiment}}\)</li>
        <li>Z-statistic and corresponding p-value</li>
        <li>95% confidence interval for the difference</li>
        <li>Clear interpretation of statistical significance</li>
    </ul>
</body>
</html>
