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
const axios = require('axios');
const options = {
  method: 'GET',
  url: 'https://dog-breeds2.p.rapidapi.com/dog_breeds',
  headers: {
    'X-RapidAPI-Key': '1748ee8916mshe4a05c6edb7af0ap1399f4jsn23f82b0ddfa3',
    'X-RapidAPI-Host': 'dog-breeds2.p.rapidapi.com'
  }
};
try {
	const response = await axios.request(options);
	console.log(response.data);
} catch (error) {
	console.error(error);
}
        $.ajax(settings).done(function (response) {
            console.log(response);
            if (response && response.response) {
                const data = response.response;
                const table = $('#covidTable').DataTable({
                    data: data,
                    columns: [
                        { data: 'breed' },
                        { data: 'origin' },
                        { data: 'height' },
                        { data: 'cases.total' },
                    ]
                });
            }
        });
    </script>
</body>

