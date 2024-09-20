<template>
    <div id="column-chart"></div>
</template>

<script>
import ApexCharts from 'apexcharts';

export default {
    name: 'MultiBarChart',
    mounted() {
        const options = {
            chart: {
                type: 'bar',
                height: 250,
                foreColor: '#FFFFFF',
            },
            plotOptions: {
                bar: {
                    horizontal: false,
                    columnWidth: '55%',
                    endingShape: 'rounded',
                },
            },
            dataLabels: {
                enabled: false,
            },
            stroke: {
                show: true,
                width: 2,
                colors: ['transparent'],
            },
            series: [
                {
                    name: 'Nuevos',
                    data: [44, 55, 57],
                    color: '#FFD700',
                },
                {
                    name: 'Renovaciones',
                    data: [76, 85, 101],
                    color: '#4682B4',
                },
            ],
            xaxis: {
                categories: ['Pendientes', 'Cerrados', 'Rechazados'],
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
            fill: {
                opacity: 1,
            },
            tooltip: {
                theme: 'dark',
                y: {
                    formatter: function (val) {
                        return '$ ' + val + ' thousands';
                    },
                },
            },
            legend: {
                labels: {
                    colors: '#FFFFFF',
                },
            },
        };

        if (
            document.getElementById('column-chart') &&
            typeof ApexCharts !== 'undefined'
        ) {
            const chart = new ApexCharts(
                document.getElementById('column-chart'),
                options
            );
            chart.render();
        }
    },
};
</script>

<style scoped>
#column-chart {
    max-width: 650px;
    margin: 35px auto;
    color: #ffffff;
}
</style>
