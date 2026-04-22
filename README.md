# 🚀 AI Skills & Future of Work - Power BI Dashboard

![Power BI](https://img.shields.io/badge/PowerBI-F2C811?style=for-the-badge&logo=Power%20BI&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Advanced-blue?style=for-the-badge)
![DataBuzz Challenge](https://img.shields.io/badge/DataBuzz-Contest_Entry-brightgreen?style=for-the-badge)

## 📌 Overview
This repository contains my submission for the **DataBuzz Power BI Challenge**. The project explores the intersection of AI skills, job automation risk, and workforce productivity. 

Instead of building a standard reporting dashboard, I focused on a full redesign challenge combining **advanced DAX problem-solving, statistical validation, and minimalist visual storytelling** to provide actionable insights into how AI tools (like Claude 3.7 Sonnet and ChatGPT-4o) are impacting global job markets.

## ✨ Key Features
* **Statistical Validation (DAX T-Test):** Engineered a dynamic Two-Sample T-Test directly within Power BI using custom DAX measures. This calculates real-time p-values to prove the statistical significance of productivity gains between different AI tools.
* **Denormalized Star Schema:** Optimized data modeling utilizing a central 58-column Fact table (`Fact_JobsAI`) surrounded by streamlined Dimension tables (Country, JobRole, Industry, AITool, Skill, Experience).
* **Minimalist UI/UX Design:** Focused on clean, professional interfaces, allowing complex statistical insights to be easily digestible for business stakeholders.
* **Dynamic Slicing:** Fully interactive filtering across Geography, Industry, Tool adoption rates, and Experience levels.

## 📊 Advanced DAX Highlight: The T-Test
One of the core technical achievements in this dashboard is calculating the **Welch's T-Test** using pure DAX to compare AI tool productivity. 
<img width="662" height="383" alt="1" src="https://github.com/user-attachments/assets/9e8bcaea-71ef-4452-b9b4-5068b2e68ab2" />
<img width="658" height="381" alt="7" src="https://github.com/user-attachments/assets/572762f1-4293-4366-9a16-2f9a9e90b6c6" />
<img width="658" height="377" alt="6" src="https://github.com/user-attachments/assets/80cbbdf8-b0b9-4160-8dd0-04c0e292b932" />
<img width="659" height="380" alt="5" src="https://github.com/user-attachments/assets/7dfa9296-3131-494d-a3d0-e85482c7dbdc" />
<img width="658" height="379" alt="4" src="https://github.com/user-attachments/assets/1b63f8e2-feae-44c4-b1bd-6847a144d0ea" />
<img width="657" height="378" alt="3" src="https://github.com/user-attachments/assets/19649808-99de-45cd-81ba-ac61becdfcb2" />
<img width="662" height="382" alt="2" src="https://github.com/user-attachments/assets/944cb846-7c11-48d1-a5d1-7c971f5396f5" />

```dax
// Example snippet of the 2-Tailed P-Value Calculation
VAR StandardError = SQRT(DIVIDE(Var_Claude, N_Claude) + DIVIDE(Var_ChatGPT, N_ChatGPT))
VAR T_Stat = DIVIDE((Mean_Claude - Mean_ChatGPT), StandardError)
VAR DF_Numerator = POWER(DIVIDE(Var_Claude, N_Claude) + DIVIDE(Var_ChatGPT, N_ChatGPT), 2)
// ... degrees of freedom calculation ...
RETURN IFERROR(T.DIST.2T(ABS(T_Stat), DF), BLANK())


