<script setup lang="ts">
import DonutChart from './components/charts/DonutChart.vue';
import MultiBarChart from './components/charts/MultiBarChart.vue';
import PieChart from './components/charts/PieChart.vue';
import SparkChart from './components/charts/SparkChart.vue';
</script>

<template>
    <div class="card-large">
        <div class="sparkline-container">
            <SparkChart />
        </div>
        <div class="charts-grid">
            <div class="chart-card large-chart">
                <h3>Propuestas en general</h3>
                <div class="chart-container">
                    <PieChart />
                </div>
            </div>
            <div class="chart-card">
                <h3>Estado/Tipos</h3>
                <div class="chart-container">
                    <MultiBarChart />
                </div>
            </div>
            <div class="chart-card large-chart">
                <h3>Propuestas Pendeintes</h3>
                <div class="chart-container">
                    <DonutChart />
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-large {
    background: #374141;
    border-radius: 8px;
    padding: 20px;
    margin: 20px auto;
    max-width: 1200px;
    color: #ffffff;
}

.sparkline-container {
    display: flex;
    justify-content: space-around;
    align-items: center;
    gap: 10px;
    margin-bottom: 20px;
    width: 100%;
}

.charts-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 1rem;
    justify-content: center;
    align-items: start;
}

.chart-card {
    background: #2a3131;
    border-radius: 8px;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    height: 320px;
    color: #ffffff;
}

.chart-card h3 {
    margin-bottom: 10px;
    color: #ffffff;
}

.chart-container {
    flex: 1;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}

.large-chart {
    max-width: 450px;
}
</style>
