<template>
<div>
    <div class="row mb-3">
        <div class="col-12 col-md-12">
            <canvas id="chart" ref="chart"></canvas>
        </div>
    </div>
    <div class="row">
        <div class="col-12 table-responsive">
            <table class="table table-striped">
                <thead>
                    <th scope="col">Data</th>
                    <th scope="col">Demanda</th>
                    <th scope="col">Capacidade</th>
                    <th scope="col">Atendimento Planejado</th>
                    <th scope="col">Atendimento Realizado</th>
                    <th scope="col">Atendimento Desvio</th>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in items" :key="index">
                        <td class="align-middle">{{ item.data }}</td>
                        <td>{{ item.demanda }}</td>
                        <td>{{ item.capacidade }}</td>
                        <td>{{ item.atendimentoPlanejado }}</td>
                        <td>{{ item.atendimentoRealizado }}</td>
                        <td>{{ item.desvio }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</div>
</template>

<script>
import Chart from 'chart.js';

export default {
    name: 'Content',
    computed: {
        items() {
            return [
                {
                    data: '20/03/2020',
                    demanda: 4,
                    capacidade: 10,
                    atendimentoPlanejado: 10,
                    atendimentoRealizado: 6,
                    desvio: 2,
                },
                {
                    data: '20/03/2020',
                    demanda: 4,
                    capacidade: 12,
                    atendimentoPlanejado: 3,
                    atendimentoRealizado: 4,
                    desvio: 4,
                },
                {
                    data: '21/03/2020',
                    demanda: 2,
                    capacidade: 30,
                    atendimentoPlanejado: 2,
                    atendimentoRealizado: 2,
                    desvio: 1,
                },
                {
                    data: '21/03/2020',
                    demanda: 10,
                    capacidade: 40,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 8,
                    desvio: 2,
                },
                {
                    data: '22/03/2020',
                    demanda: 15,
                    capacidade: 30,
                    atendimentoPlanejado: 10,
                    atendimentoRealizado: 4,
                    desvio: 3,
                },
                {
                    data: '22/03/2020',
                    demanda: 10,
                    capacidade: 30,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 24,
                    desvio: 1,
                },
                {
                    data: '22/03/2020',
                    demanda: 10,
                    capacidade: 30,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 24,
                    desvio: 1,
                },
                {
                    data: '22/03/2020',
                    demanda: 10,
                    capacidade: 30,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 24,
                    desvio: 1,
                },
                {
                    data: '22/03/2020',
                    demanda: 10,
                    capacidade: 30,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 24,
                    desvio: 1,
                },
                {
                    data: '22/03/2020',
                    demanda: 10,
                    capacidade: 30,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 24,
                    desvio: 1,
                },
                {
                    data: '22/03/2020',
                    demanda: 10,
                    capacidade: 30,
                    atendimentoPlanejado: 8,
                    atendimentoRealizado: 24,
                    desvio: 1,
                },
            ]
        }
    },
    methods: {
        onlyUnique(array, key) {
            let output = [];
            const length = array.length;

            for(let i = 0; i < length; i++) {
                if(output.indexOf(array[i][key]) !== -1) continue;
                output.push(array[i][key]);
            }

            return output;
        },
        sum(dates, array) {
            let output = {};
            const length = dates.length;

            for(let i = 0; i < length; i++) {
                const currentDate = dates[i];
                const total = array.filter(a => a.data === currentDate)
                                .reduce((carry, item) => (carry + (item.capacidade - item.atendimentoRealizado)), 0);
                output[currentDate] = total;
            }

            return output;
        },
    },
    mounted() {
        const ctx = this.$refs.chart;
        // x datas
        // y diferença entre valores de capacidade e atendimentos realizados
        const dates = this.onlyUnique(this.items, 'data');
        const sumOfDates = this.sum(dates, this.items);
        const values = Object.values(sumOfDates);
        new Chart(ctx, {
            type: 'bar',
            data: {
                labels: dates,
                datasets: [{
                    label: 'Capacidade - Atendimento Realizado',
                    data: values,
                    backgroundColor: 'rgba(54, 162, 235, 0.7)',
                    borderColor: 'rgba(54, 162, 235, 1)',
                    borderWidth: 1
                }]
            },
            options: {
                scales: {
                    yAxes: [{
                        ticks: {
                            beginAtZero: true
                        }
                    }]
                }
            }
        });
    }
}
</script>

<style scoped>

</style>
