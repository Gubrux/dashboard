<template>
    <div id="pie-chart" class="chart-container"></div>
</template>

<script>
import ApexCharts from 'apexcharts';

export default {
    name: 'PieChart',
    mounted() {
        const options = {
            chart: {
                type: 'pie',
                height: 400,
            },
            series: [44, 55, 13],
            labels: ['Team A', 'Team B', 'Team C'],
            colors: [
                '#4682B4', 
                '#FF6347', 
                '#FFD700', 
            ],
            responsive: [
                {
                    breakpoint: 480,
                    options: {
                        chart: {
                            width: 400,
                        },
                        legend: {
                            position: 'bottom',
                            labels: {
                                colors: '#FFFFFF',
                            },
                        },
                    },
                },
            ],
            legend: {
                labels: {
                    colors: ['#4682B4', '#FF6347', '#FFD700'],
                },
            },
            dataLabels: {
                style: {
                    colors: ['#FFFFFF'],
                },
            },
            tooltip: {
                theme: 'dark',
            },
        };

        if (
            document.getElementById('pie-chart') &&
            typeof ApexCharts !== 'undefined'
        ) {
            const chart = new ApexCharts(
                document.getElementById('pie-chart'),
                options
            );
            chart.render();
        }
    },
};
</script>

<style scoped>
.chart-container {
    width: 400px;
    margin: 0 auto;
    color: #ffffff;
}
</style>
