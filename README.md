# Adaptive OS Scheduler for Real-Time Systems

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://adaptive-os-scheduler-one.vercel.app/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Scheduling Algorithms](#scheduling-algorithms)
- [Visualizations](#visualizations)
- [Getting Started](#getting-started)
- [Usage Guide](#usage-guide)
- [Project Structure](#project-structure)
- [Technical Implementation](#technical-implementation)
- [Browser Compatibility](#browser-compatibility)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## 🎯 Overview

This project implements an **Adaptive Operating System Scheduler** specifically designed for real-time systems. The scheduler dynamically adjusts task priorities to optimize system performance based on workload characteristics and deadline constraints. It provides an interactive web-based interface for visualizing and comparing two fundamental real-time scheduling algorithms: **Rate-Monotonic Scheduling (RMS)** and **Earliest Deadline First (EDF)**.

### Key Objectives

- Demonstrate real-time scheduling concepts through interactive visualization
- Compare static vs. dynamic priority scheduling approaches
- Provide educational insights into CPU scheduling algorithms
- Enable hands-on experimentation with task parameters

## ✨ Features

### Core Functionality

- **Dynamic Priority Adjustment**: Real-time modification of task priorities based on system state
- **Dual Algorithm Support**: Implementation of both RMS and EDF scheduling
- **Interactive Task Management**: Add, edit, and delete tasks with custom parameters
- **Real-Time Visualization**: Multiple visualization modes including Gantt charts, pie charts, and bar graphs
- **Comparative Analysis**: Side-by-side comparison of EDF vs RMS performance
- **Hyperperiod Calculation**: Automatic computation of LCM for periodic task scheduling

### Visualization Features

- **Gantt Chart**: Timeline view showing task execution sequence
- **Pie Chart**: Proportional CPU time allocation with animated current task highlighting
- **Bar Graph**: Comparative view of task time allocation with percentage metrics
- **Dynamic Animation**: Real-time updates showing current task execution (1 second intervals)
- **Color-Coded Tasks**: Visual distinction between different tasks and idle time

### User Interface

- **Responsive Design**: Mobile-friendly interface using Tailwind CSS
- **Intuitive Controls**: Easy-to-use task input forms
- **Real-Time Feedback**: Immediate visual updates on task modifications
- **Clean Layout**: Professional design with clear information hierarchy

## 🔄 Scheduling Algorithms

### Rate-Monotonic Scheduling (RMS)

**Type**: Fixed-Priority Preemptive Scheduling

**Priority Assignment**: Tasks with shorter periods receive higher priority

**Characteristics**:
- Static priority assignment based on task periodicity
- Optimal among fixed-priority algorithms
- Predictable and deterministic behavior
- Best suited for periodic tasks with fixed deadlines
- Schedulability bound: U ≤ n(2^(1/n) - 1), where n is the number of tasks

**Use Cases**:
- Embedded systems with predictable workloads
- Safety-critical applications requiring deterministic behavior
- Systems with periodic tasks and fixed timing requirements

### Earliest Deadline First (EDF)

**Type**: Dynamic-Priority Preemptive Scheduling

**Priority Assignment**: Tasks with earlier absolute deadlines receive higher priority

**Characteristics**:
- Dynamic priority adjustment based on current deadlines
- Optimal among all scheduling algorithms for single processor
- Higher CPU utilization possible (up to 100%)
- More flexible for varying workloads
- Schedulability condition: U ≤ 1, where U is total utilization

**Use Cases**:
- Systems with varying task deadlines
- Applications requiring maximum CPU utilization
- Dynamic workload environments
- Soft real-time systems

## 📊 Visualizations

### 1. Gantt Chart
Displays the execution timeline of tasks across the hyperperiod, showing:
- Task execution intervals
- Context switches
- Idle time periods
- Time axis with millisecond precision

### 2. Pie Chart (Animated)
Shows proportional CPU time allocation:
- Percentage breakdown for each task
- Current running task highlighted with bold border
- Color-coded legend
- Real-time animation (updates every second)

### 3. Bar Graph (Animated)
Comparative visualization featuring:
- Vertical bars representing time allocation
- Percentage labels on bars
- Absolute time values (in milliseconds)
- Current task highlighting
- Y-axis labeling for clarity

### 4. Comparison Mode
Side-by-side visualization of EDF vs RMS:
- Synchronized animations
- Parallel Gantt charts
- Dual pie charts
- Dual bar graphs
- Unified time counter

## 🚀 Getting Started

### Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- No server setup required - runs entirely in the browser
- JavaScript enabled

### Installation

1. **Make folder and the repository**
   ```bash
   cd OsProject
   ```

2. **Open in browser**
   ```bash
   # Simply open index.html in your browser
   # Or use a local server (optional)
   python -m http.server 8000
   # Then navigate to http://localhost:8000
   ```

3. **Access the live demo**
   
   Visit: [https://adaptive-os-scheduler-one.vercel.app/](https://adaptive-os-scheduler-one.vercel.app/)

## 📖 Usage Guide

### Adding Tasks

1. Navigate to the scheduler page
2. Fill in the task parameters:
   - **Task ID**: Unique identifier (integer)
   - **Execution Time**: Time required to complete the task (in milliseconds)
   - **Deadline**: Task deadline (optional for RMS, defaults to period)
   - **Period**: Task repetition interval (in milliseconds)
3. Click "Add Task" to add to the queue

### Running Schedulers

**Single Algorithm Mode**:
- Click "Run EDF Scheduler" for Earliest Deadline First
- Click "Run RMS Scheduler" for Rate-Monotonic Scheduling
- View results in output panel, Gantt chart, pie chart, and bar graph

**Comparison Mode**:
- Click "EDF vs RMS" to compare both algorithms
- View side-by-side visualizations
- Observe differences in task scheduling and CPU allocation

### Managing Tasks

- **Edit Task**: Click the "Edit" button on any task to modify parameters
- **Delete Task**: Click the "Delete" button to remove a task
- **Clear All**: Click "Clear Tasks" to reset the task queue

### Understanding Output

**Scheduler Output Panel**:
```
EDF Scheduling Output (Hyperperiod: 60ms):
Priority: Earlier Deadline = Higher Priority
time 0.0 to 3.0: task 1
time 3.0 to 6.0: task 2
time 6.0 to 10.0: task 1
...
```

**Gantt Chart**: Visual timeline of task execution

**Pie Chart**: Shows percentage allocation (e.g., Task 1: 45%, Task 2: 35%, idle: 20%)

**Bar Graph**: Comparative bars with exact time values

## 📁 Project Structure

```
OsProject/
│
├── index.html              # Landing page with project overview
├── scheduler.html          # Main scheduler interface and implementation
├── README.md              # Project documentation
│
├── .git/                  # Git version control
│
└── assets/                # (Optional) Images and resources
```

### File Descriptions

#### `index.html`
- Landing page with project introduction
- Feature highlights
- Algorithm explanations
- Navigation to scheduler
- Contact form

#### `scheduler.html`
- Complete scheduler implementation
- Task management interface
- Scheduling algorithm logic
- Visualization components (Gantt, Pie, Bar)
- Animation controllers
- Responsive layout

## 🔧 Technical Implementation

### Core Technologies

- **HTML5**: Semantic markup and structure
- **CSS3**: Styling via Tailwind CSS framework
- **JavaScript (ES6+)**: Scheduling logic and animations
- **Canvas API**: Chart rendering and animations

### Key Algorithms

#### Hyperperiod Calculation
```javascript
function getHyperperiod() {
  // Calculate LCM of all task periods
  let hyper = tasks[0].period;
  for (let i = 1; i < tasks.length; i++) {
    hyper = lcm(hyper, tasks[i].period);
  }
  return hyper;
}
```

#### Task Scheduling Logic
```javascript
// EDF: Sort by deadline
available.sort((a, b) => a.nextDeadline - b.nextDeadline);

// RMS: Sort by period
available.sort((a, b) => a.period - b.period);
```

#### Animation System
- Interval-based updates (1000ms)
- Synchronized multi-chart rendering
- Looping through hyperperiod
- Dynamic task highlighting

### Data Structures

**Task Object**:
```javascript
{
  id: number,
  executionTime: number,
  deadline: number,
  period: number,
  remaining: number,
  nextArrival: number,
  nextDeadline: number
}
```

**Event Object**:
```javascript
{
  start: number,
  end: number,
  label: string
}
```

## 🌐 Browser Compatibility

| Browser | Version | Status |
|---------|---------|--------|
| Chrome  | 90+     | ✅ Fully Supported |
| Firefox | 88+     | ✅ Fully Supported |
| Safari  | 14+     | ✅ Fully Supported |
| Edge    | 90+     | ✅ Fully Supported |
| Opera   | 76+     | ✅ Fully Supported |

### Requirements
- JavaScript enabled
- HTML5 Canvas support
- ES6+ JavaScript support

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
5. **Open a Pull Request**

### Contribution Ideas

- Add more scheduling algorithms (FCFS, SJF, Priority Scheduling)
- Implement deadline miss detection
- Add CPU utilization metrics
- Export scheduling results to CSV/JSON
- Add task preemption cost simulation
- Implement multi-core scheduling
- Add dark mode theme
- Improve mobile responsiveness

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Real-Time Systems Theory**: Based on classical scheduling algorithms from operating systems literature
- **Tailwind CSS**: For the beautiful and responsive UI framework
- **Canvas API**: For enabling rich visualizations
- **Open Source Community**: For inspiration and best practices

## 📞 Contact

For questions, suggestions, or feedback:

- **GitHub Issues**: [Create an issue](https://adaptive-os-scheduler-one.vercel.app/issues)
- **Live Demo**: [Adaptive-Os-Scheduler](https://adaptive-os-scheduler-one.vercel.app/)

---

**Made with ❤️ for Real-Time Systems Education**

*Last Updated: 2025*
