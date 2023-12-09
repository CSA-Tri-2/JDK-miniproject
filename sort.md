---
toc: true
layout: post
title: Fibonacci
description: 
courses: { compsci: {week: 1} }
type: hacks
---
<head>
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>var define = null;</script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<body>
    <table id="covidTable" class="display" style="width:100%">
        <thead>
            <tr>
                <th>Country</th>
                <th>Continent</th>
                <th>New Cases</th>
                <th>Total Cases</th>
            </tr>
        </thead>
        <tbody>
        </tbody>
    </table>
    <script>
        const settings = {
            async: true,
            crossDomain: true,
            url: 'https://covid-193.p.rapidapi.com/statistics',
            method: 'GET',
            headers: {
                'X-RapidAPI-Key': '1748ee8916mshe4a05c6edb7af0ap1399f4jsn23f82b0ddfa3',
                'X-RapidAPI-Host': 'covid-193.p.rapidapi.com'
            }
        };
        $.ajax(settings).done(function (response) {
            console.log(response);
            if (response && response.response && response.response.length > 0) {
                const data = response.response;
                // Extract and shuffle the array of countries using vanilla JavaScript
                const shuffledData = data.slice().sort(() => Math.random() - 0.5);
                const table = $('#covidTable').DataTable({
                    columns: [
                        { data: 'country' },
                        { data: 'continent' },
                        { data: 'cases.new' },
                        { data: 'cases.total' },
                    ]
                });
                // Add the shuffled data to the DataTable
                table.rows.add(shuffledData).draw();
            }
        });
    </script>
</body>
