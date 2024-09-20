<template>
    <div class="sparkline-container">
        <div class="card">
            <div id="chart-spark1" class="sparkline-chart"></div>
        </div>
        <!-- <div class="card">
            <div id="chart-spark2" class="sparkline-chart"></div>
        </div>
        <div class="card">
            <div id="chart-spark3" class="sparkline-chart"></div>
        </div> -->
    </div>
</template>

<script>
import ApexCharts from 'apexcharts';

export default {
    name: 'SparklineChart',
    mounted() {
        const sparklineData = [10, 15, 14, 20, 18, 25, 22, 30, 28, 35, 32, 40];
        const meses = [
            'Ene',
            'Feb',
            'Mar',
            'Abr',
            'May',
            'Jun',
            'Jul',
            'Ago',
            'Sep',
            'Oct',
            'Nov',
            'Dic',
        ];
        const randomizeArray = (arg) => {
            const array = arg.slice().map((item, index) => {
                return {
                    y: item,
                    x: meses[index],
                };
            });
            let currentIndex = array.length,
                temporaryValue,
                randomIndex;

            while (0 !== currentIndex) {
                randomIndex = Math.floor(Math.random() * currentIndex);
                currentIndex -= 1;
                temporaryValue = array[currentIndex].y;
                array[currentIndex].y = array[randomIndex].y;
                array[randomIndex] = {
                    y: temporaryValue,
                    x: meses[randomIndex],
                };
            }
            console.log(array);
            return array;
        };

        const options1 = {
            chart: {
                height: 280,
                type: 'area',
                stacked: true,
            },
            stroke: { curve: 'straight' },
            dataLabels: {
                enabled: false,
            },
            series: [
                {
                    name: 'Cerrados',
                    data: [45, 52, 38, 45, 19, 23, 2, 45, 23, 56, 23, 45],
                    color: '#4682B4',
                },
                {
                    name: 'Rechazados',
                    data: [11, 22, 15, 13, 19, 17, 27, 18, 12, 19, 23, 14],
                    color: '#FF6347',
                },
                {
                    name: 'Pendientes',
                    data: [45, 52, 38, 45, 19, 23, 2, 45, 23, 56, 23, 45],
                    color: '#FFD700',
                },
            ],
            legend: {
                labels: {
                    colors: ['#4682B4', '#FF6347', '#FFD700'],
                },
            },
            title: {
                text: 'Comparación de Propuestas',
                offsetX: 0,
                style: { fontSize: '14px', color: '#FFFFFF' },
            },
            subtitle: {
                text: 'Por estado',
                offsetX: 0,
                style: { fontSize: '14px', color: '#FFFFFF' },
            },
            fill: {
                type: 'gradient',
                gradient: {
                    shadeIntensity: 1,
                    opacityFrom: 0.2,
                    opacityTo: 0.4,
                    stops: [0, 90, 100],
                    
                },
            },
            xaxis: {
                categories: meses,
                labels: {
                    style: {
                        colors: '#FFFFFF',
                    },
                },
            },
            yaxis: {
                labels: {
                    style: {
                        colors: '#FFFFFF',
                    },
                },
            },
        };

        const chart1 = new ApexCharts(
            document.querySelector('#chart-spark1'),
            options1
        );
        chart1.render();

        const options2 = {
            series: [{ data: randomizeArray(sparklineData) }],
            chart: {
                type: 'area',
                height: 160,
                sparkline: { enabled: true },
            },
            stroke: { curve: 'straight' },
            fill: { opacity: 0.3 },
            yaxis: { min: 0 },
            colors: ['#FF7518'],
            title: {
                text: '$235,312',
                offsetX: 0,
                style: { fontSize: '24px', color: '#FFFFFF' },
            },
            subtitle: {
                text: 'Rechazados',
                offsetX: 0,
                style: { fontSize: '14px', color: '#FFFFFF' },
            },
        };

        const chart2 = new ApexCharts(
            document.querySelector('#chart-spark2'),
            options2
        );
        chart2.render();

        const options3 = {
            series: [{ data: randomizeArray(sparklineData) }],
            chart: {
                type: 'area',
                height: 160,
                sparkline: { enabled: true },
            },
            stroke: { curve: 'straight' },
            fill: { opacity: 0.3 },
            xaxis: { crosshairs: { width: 1 } },
            yaxis: { min: 0 },
            title: {
                text: '$135,965',
                offsetX: 0,
                style: { fontSize: '24px', color: '#FFFFFF' },
            },
            subtitle: {
                text: 'Cerrados',
                offsetX: 0,
                style: { fontSize: '14px', color: '#FFFFFF' },
            },
        };

        const chart3 = new ApexCharts(
            document.querySelector('#chart-spark3'),
            options3
        );
        chart3.render();
    },
};
</script>

<style scoped>
.sparkline-container {
    display: flex;
    justify-content: space-around;
    align-items: center;
    gap: 10px;
}

.card {
    background: #2a3131;
    border-radius: 8px;
    padding: 20px;
    flex: 1;
    max-width: 450px;
    margin: 10px;
    color: #373534;
}

.sparkline-chart {
    margin: 10px 0;
}
</style>
