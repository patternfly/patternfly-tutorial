# PatternFly Tutorial

This guide will help you set up PatternFly and start a PatternFly dashboard.

The first step is to fork and clone the quick start repo:

https://github.com/andresgalante/patternfly-quickstart

Once you have it, `cd` into your project folder and install the dependencies:

```bash
npm install
```

This will get you patternfly and all the dev dependencies.

Now start browsersync by running

```bash
gulp
```

This will start a server at [http://localhost:3000/](http://localhost:3000/) and it will auto fresh every time you modify your HTML or CSS.

## PatternFly CSS

Open `index.html` on your favorite text editor. You'll notice that you are importing `patternfly.min.css` and `patternfly-additions-min.css`

Patternfly is based on bootstrap. patternfly.css is our customizations of bootstrap styles and additions is everything else we've added to support out enterprise usecases.

```html
  <link rel="stylesheet" href="node_modules/patternfly/dist/css/patternfly.min.css">
  <link rel="stylesheet" href="node_modules/patternfly/dist/css/patternfly-additions.min.css">
```

This page is ready to use any patternfly component. You cna go to ther website, copy any spinnet and use it. But I'll guide you step by step to build a dashboard, and customize patternfly.

### The Grid

Bootstrap offers a [responsive 12 column grid system](http://getbootstrap.com/css/#grid).

Let's start by building a grid structure to accomodate our components:

```html
<body>
<!-- PatternFly Horizontal Nav -->

  <div class="container-fluid">
    <div class="row">

      <div class="col-xs-6 col-sm-4 col-md-2">
        <!-- Aggregated status card -->
      </div><!-- /col -->

      <div class="col-xs-6 col-sm-4 col-md-2">
        <!-- Aggregated status card -->
      </div><!-- /col -->

      <div class="col-xs-6 col-sm-4 col-md-2">
        <!-- Aggregated status card -->
      </div><!-- /col -->

      <div class="col-xs-6 col-sm-4 col-md-2">
        <!-- Aggregated status card -->
      </div><!-- /col -->

      <div class="col-xs-6 col-sm-4 col-md-2">
        <!-- Aggregated status card -->
      </div><!-- /col -->

      <div class="col-xs-6 col-sm-4 col-md-2">
        <!-- Aggregated status card -->
      </div><!-- /col -->

      <div class="col-xs-12 col-md-8">
        <!-- Utilization Trend Card -->
      </div><!-- /col -->

      <div class="col-xs-12 col-md-4">
        <!-- Utilization Bar Card -->
      </div><!-- /col -->

    </div><!-- /row -->
  </div><!-- /container -->
</body>
```

### Preparation for cards layout

To initiate the card layout and adjust the spaces we'll add some patternfly specific classes to the grid and the `body`

```html
<body class="cards-pf">
  ...
  <div class="container-fluid container-cards-pf">
    <div class="row row-cards-pf">
      ...
    </div><!-- /row -->
  </div><!-- /container -->
</body>
```

### Navigation

For this example I'll be using a simple horizontal navigation, but keep in mind you can nest more levels or even use a vertical nav.

PatternFly horizontal navigation is a modified version of Bootstrap navbar.

Go to the beguining of the document, copy and paste this snippet:

```html
<!-- PatternFly Horizontal Nav -->
  <nav class="navbar navbar-default navbar-pf" role="navigation">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse-1">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="/">
        <img src="node_modules/patternfly/dist/img/brand.svg" alt="PatternFly Enterprise Application" />
      </a>
    </div>
    <div class="collapse navbar-collapse navbar-collapse-1">
      <ul class="nav navbar-nav navbar-utility">
        <li>
          <a href="#">Status</a>
        </li>
        <li class="dropdown">
          <a href="#" class="dropdown-toggle" data-toggle="dropdown">
            <span class="pficon pficon-user"></span>
            Brian Johnson <b class="caret"></b>
          </a>
          <ul class="dropdown-menu">
            <li>
              <a href="#">Link</a>
            </li>
            <li>
              <a href="#">Another link</a>
            </li>
            <li>
              <a href="#">Something else here</a>
            </li>
            <li class="divider"></li>
            <li class="dropdown-submenu">
              <a tabindex="-1" href="#">More options</a>
              <ul class="dropdown-menu">
                <li>
                  <a href="#">Link</a>
                </li>
                <li>
                  <a href="#">Another link</a>
                </li>
                <li>
                  <a href="#">Something else here</a>
                </li>
                <li class="divider"></li>
                <li class="dropdown-header">Nav header</li>
                <li>
                  <a href="#">Separated link</a>
                </li>
                <li class="divider"></li>
                <li>
                  <a href="#">One more separated link</a>
                </li>
              </ul>
            </li>
            <li class="divider"></li>
            <li>
              <a href="#">One more separated link</a>
            </li>
          </ul>
        </li>
      </ul>
      <ul class="nav navbar-nav navbar-primary">
        <li>
          <a href="#">First Link</a>
        </li>
        <li class="active">
          <a href="#">Another Link</a>
        </li>
        <li>
          <a href="#">And Another</a>
        </li>
        <li>
          <a href="#">As a General Rule</a>
        </li>
        <li>
          <a href="#">Five to Seven Links</a>
        </li>
        <li>
          <a href="#">Is Good</a>
        </li>
      </ul>
    </div>
  </nav>
  ```

### Aggregated status cards

Aggregated status cards comes in diferent flavors. For this example we'll use the "Mini Card Alternate". We have six slots to add them.

Copy and paste these snippets on the 6 spaces for Aggregated status cards, they are all slighly diferent but for the sake of the example it's ok if you repeat them:

```html
<!-- Aggregated status card -->
<div class="card-pf card-pf-accented card-pf-aggregate-status">
  <h2 class="card-pf-title">
    <span class="fa fa-shield"></span><span class="card-pf-aggregate-status-count">0</span> Ipsum
  </h2>
  <div class="card-pf-body">
    <p class="card-pf-aggregate-status-notifications">
      <span class="card-pf-aggregate-status-notification"><a href="#" class="add" data-toggle="tooltip" data-placement="top" title="Add Ipsum"><span class="pficon pficon-add-circle-o"></span></a></span>
    </p>
  </div>
</div>
```

```html
<!-- Aggregated status card -->
<div class="card-pf card-pf-accented card-pf-aggregate-status">
  <h2 class="card-pf-title">
    <a href="#"><span class="fa fa-shield"></span><span class="card-pf-aggregate-status-count">20</span> Amet</a>
  </h2>
  <div class="card-pf-body">
    <p class="card-pf-aggregate-status-notifications">
      <span class="card-pf-aggregate-status-notification"><a href="#"><span class="pficon pficon-error-circle-o"></span>4</a></span>
      <span class="card-pf-aggregate-status-notification"><a href="#"><span class="pficon pficon-warning-triangle-o"></span>1</a></span>
    </p>
  </div>
</div>
```

```html
<!-- Aggregated status card -->
<div class="card-pf card-pf-accented card-pf-aggregate-status">
  <h2 class="card-pf-title">
    <a href="#"><span class="fa fa-shield"></span><span class="card-pf-aggregate-status-count">9</span> Adipiscing</a>
  </h2>
  <div class="card-pf-body">
    <p class="card-pf-aggregate-status-notifications">
      <span class="card-pf-aggregate-status-notification"><span class="pficon pficon-ok"></span></span>
    </p>
  </div>
</div>
```

### Utilization Trend Card

We'll add 2 typs of utilization cards, let's start with trend.

Look for the next avaliable column, it's labled as `Utilization Trend Card`, and paste this snippet:

```html
<!-- Utilization Trend Card -->
<div class="card-pf card-pf-utilization">
  <div class="card-pf-heading">
    <p class="card-pf-heading-details">Last 30 days</p>
    <h2 class="card-pf-title">
      Utilization
    </h2>
  </div>
  <div class="card-pf-body">
    <div class="row">
      <div class="col-xs-12 col-sm-4 col-md-4">
        <h3 class="card-pf-subtitle">CPU</h3>
        <p class="card-pf-utilization-details">
          <span class="card-pf-utilization-card-details-count">50</span>
          <span class="card-pf-utilization-card-details-description">
            <span class="card-pf-utilization-card-details-line-1">Available</span>
            <span class="card-pf-utilization-card-details-line-2">of 1000 MHz</span>
          </span>
        </p>
        <div id="chart-pf-donut-6"></div>
        <div class="chart-pf-sparkline" id="chart-pf-sparkline-6"></div>
        <script>
        var donutConfig = $().c3ChartDefaults().getDefaultDonutConfig('A');
        donutConfig.bindto = '#chart-pf-donut-6';
        donutConfig.color =  {
          pattern: ["#cc0000","#D1D1D1"]
        };
        donutConfig.data = {
          type: "donut",
          columns: [
            ["Used", 95],
            ["Available", 5]
          ],
          groups: [
            ["used", "available"]
          ],
          order: null
        };
        donutConfig.tooltip = {
          contents: function (d) {
            return '<span class="donut-tooltip-pf" style="white-space: nowrap;">' +
            Math.round(d[0].ratio * 100) + '%' + ' MHz ' + d[0].name +
            '</span>';
          }
        };

        var chart1 = c3.generate(donutConfig);
        var donutChartTitle = d3.select("#chart-pf-donut-6").select('text.c3-chart-arcs-title');
        donutChartTitle.text("");
        donutChartTitle.insert('tspan').text("950").classed('donut-title-big-pf', true).attr('dy', 0).attr('x', 0);
        donutChartTitle.insert('tspan').text("MHz Used").classed('donut-title-small-pf', true).attr('dy', 20).attr('x', 0);

        var sparklineConfig = $().c3ChartDefaults().getDefaultSparklineConfig();
        sparklineConfig.bindto = '#chart-pf-sparkline-6';
        sparklineConfig.data = {
          columns: [
            ['%', 10, 50, 28, 20, 31, 27, 60, 36, 52, 55, 62, 68, 69, 88, 74, 88, 95],
          ],
          type: 'area'
        };
        var chart2 = c3.generate(sparklineConfig);
        </script>
      </div>
      <div class="col-xs-12 col-sm-4 col-md-4">
        <h3 class="card-pf-subtitle">Memory</h3>
        <p class="card-pf-utilization-details">
          <span class="card-pf-utilization-card-details-count">256</span>
          <span class="card-pf-utilization-card-details-description">
            <span class="card-pf-utilization-card-details-line-1">Available</span>
            <span class="card-pf-utilization-card-details-line-2">of 432 GB</span>
          </span>
        </p>
        <div id="chart-pf-donut-7"></div>
        <div class="chart-pf-sparkline" id="chart-pf-sparkline-7"></div>
        <script>
        var donutConfig = $().c3ChartDefaults().getDefaultDonutConfig('A');
        donutConfig.bindto = '#chart-pf-donut-7';
        donutConfig.color =  {
          pattern: ["#3f9c35","#D1D1D1"]
        };
        donutConfig.data = {
          type: "donut",
          columns: [
            ["Used", 41],
            ["Available", 59]
          ],
          groups: [
            ["used", "available"]
          ],
          order: null
        };
        donutConfig.tooltip = {
          contents: function (d) {
            return '<span class="donut-tooltip-pf" style="white-space: nowrap;">' +
            Math.round(d[0].ratio * 100) + '%' + ' GB ' + d[0].name +
            '</span>';
          }
        };

        var chart3 = c3.generate(donutConfig);
        var donutChartTitle = d3.select("#chart-pf-donut-7").select('text.c3-chart-arcs-title');
        donutChartTitle.text("");
        donutChartTitle.insert('tspan').text("176").classed('donut-title-big-pf', true).attr('dy', 0).attr('x', 0);
        donutChartTitle.insert('tspan').text("GB Used").classed('donut-title-small-pf', true).attr('dy', 20).attr('x', 0);

        var sparklineConfig = $().c3ChartDefaults().getDefaultSparklineConfig();
        sparklineConfig.bindto = '#chart-pf-sparkline-7';
        sparklineConfig.data = {
          columns: [
            ['%', 35, 36, 20, 30, 31, 22, 44, 36, 40, 41, 55, 52, 48, 48, 50, 40, 41],
          ],
          type: 'area'
        };
        var chart4 = c3.generate(sparklineConfig);
        </script>
      </div>
      <div class="col-xs-12 col-sm-4 col-md-4">
        <h3 class="card-pf-subtitle">Network</h3>
        <p class="card-pf-utilization-details">
          <span class="card-pf-utilization-card-details-count">200</span>
          <span class="card-pf-utilization-card-details-description">
            <span class="card-pf-utilization-card-details-line-1">Available</span>
            <span class="card-pf-utilization-card-details-line-2">of 1300 Gbps</span>
          </span>
        </p>
        <div id="chart-pf-donut-8"></div>
        <div class="chart-pf-sparkline" id="chart-pf-sparkline-8"></div>
        <script>
        var donutConfig = $().c3ChartDefaults().getDefaultDonutConfig('A');
        donutConfig.bindto = '#chart-pf-donut-8';
        donutConfig.color =  {
          pattern: ["#EC7A08","#D1D1D1"]
        };
        donutConfig.data = {
          type: "donut",
          columns: [
            ["Used", 85],
            ["Available", 15]
          ],
          groups: [
            ["used", "available"]
          ],
          order: null
        };
        donutConfig.tooltip = {
          contents: function (d) {
            return '<span class="donut-tooltip-pf" style="white-space: nowrap;">' +
            Math.round(d[0].ratio * 100) + '%' + ' Gbps ' + d[0].name +
            '</span>';
          }
        };

        var chart5 = c3.generate(donutConfig);
        var donutChartTitle = d3.select("#chart-pf-donut-8").select('text.c3-chart-arcs-title');
        donutChartTitle.text("");
        donutChartTitle.insert('tspan').text("1100").classed('donut-title-big-pf', true).attr('dy', 0).attr('x', 0);
        donutChartTitle.insert('tspan').text("Gbps Used").classed('donut-title-small-pf', true).attr('dy', 20).attr('x', 0);

        var sparklineConfig = $().c3ChartDefaults().getDefaultSparklineConfig();
        sparklineConfig.bindto = '#chart-pf-sparkline-8';
        sparklineConfig.data = {
          columns: [
            ['%', 60, 55, 70, 44, 31, 67, 54, 46, 58, 75, 62, 68, 69, 88, 74, 88, 85],
          ],
          type: 'area'
        };
        var chart6 = c3.generate(sparklineConfig);
        </script>
      </div>
    </div>
  </div>
</div>
```

This snippet container charts, don't worry that they don't work yet, we'll add the javascript later.

### Utilization Bar Card

Now it's the trun to add an Utilization Bar Card, copy this snipptet and past it the last empty column:

```html
<!-- Utilization Bar Card -->
<div class="card-pf">
  <div class="card-pf-heading">
    <h2 class="card-pf-title">
      Top Utilized Clusters
    </h2>
  </div>
  <div class="card-pf-body">
    <div class="progress-description">
      RHOS6-Controller
    </div>
    <div class="progress progress-label-top-right">
      <div class="progress-bar progress-bar-danger" role="progressbar" aria-valuenow="95" aria-valuemin="0" aria-valuemax="100" style="width: 95%;"  data-toggle="tooltip" title="95% Used">
        <span><strong>190.0 of 200.0 GB</strong> Used</span>
      </div>
      <div class="progress-bar progress-bar-remaining" role="progressbar" aria-valuenow="5" aria-valuemin="0" aria-valuemax="100" style="width: 5%;" data-toggle="tooltip" title="5% Available">
        <span class="sr-only">5% Available</span>
      </div>
    </div>
    <div class="progress-description">
      CFMEQE-Cluster
    </div>
    <div class="progress progress-label-top-right">
      <div class="progress-bar progress-bar-success" role="progressbar" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100" style="width: 50%;"  data-toggle="tooltip" title="50% Used">
        <span><strong>100.0 of 200.0 GB</strong> Used</span>
      </div>
      <div class="progress-bar progress-bar-remaining" role="progressbar" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100" style="width: 50%;" data-toggle="tooltip" title="50% Available">
        <span class="sr-only">50% Available</span>
      </div>
    </div>
    <div class="progress-description">
      RHOS-Undercloud
    </div>
    <div class="progress progress-label-top-right">
      <div class="progress-bar progress-bar-warning" role="progressbar" aria-valuenow="70" aria-valuemin="0" aria-valuemax="100" style="width: 70%;"  data-toggle="tooltip" title="70% Used">
        <span><strong>140.0 of 200.0 GB</strong> Used</span>
      </div>
      <div class="progress-bar progress-bar-remaining" role="progressbar" aria-valuenow="30" aria-valuemin="0" aria-valuemax="100" style="width: 30%;" data-toggle="tooltip" title="30% Available">
        <span class="sr-only">30% Available</span>
      </div>
    </div>
    <div class="progress-description">
      RHEL6-Controller
    </div>
    <div class="progress progress-label-top-right">
      <div class="progress-bar progress-bar-warning" role="progressbar" aria-valuenow="76.5" aria-valuemin="0" aria-valuemax="100" style="width: 76.5%;"  data-toggle="tooltip" title="76.5% Used">
        <span><strong>153.0 of 200.0 GB</strong> Used</span>
      </div>
      <div class="progress-bar progress-bar-remaining" role="progressbar" aria-valuenow="23.5" aria-valuemin="0" aria-valuemax="100" style="width: 23.5%;" data-toggle="tooltip" title="23.5% Available">
        <span class="sr-only">23.5% Available</span>
      </div>
    </div>
  </div>
</div>
```

## Responsive

As I mention before Bootstrap and PatternFly are reponsive, try now to resize the browser window and see how the content reacomodates as it hits the brakepoints.

## Javascript

Brian will write something about adding D3, C3, patternfly, jquery, bootstrap and matchhieght JS

## Customize your app

The best way to customize patternfly styles is to extendend it instead of overwritting it. By extending PatternFly's and Bootstrap's styles, you'll be able to use and change all their mixing and variables.

Bootstrap and PatternFly use Less to preprocess their CSS. This repo is setup to compile LESS into CSS.

### Load the compiled CSS

On your HTML comment out patternfly's CSS and uncoment the compiled CSS

```html

<!-- PatternFly Styles -->
<!-- <link rel="stylesheet" href="node_modules/patternfly/dist/css/patternfly.min.css"> -->
<!-- <link rel="stylesheet" href="node_modules/patternfly/dist/css/patternfly-additions.min.css"> -->

<!-- Bootstrap base + PatternFly extensions + Your styles -->
<link rel="stylesheet" href="css/mystyles.css">
```

### Change Less variables

Now open `less/mystyles.less`

You should put all your styles here.

You can change any variable, for example to change the colors of all links:

```less
@link-color: orange;
```

But we don't recommend changing the variables since they have been carefully crafted by skilfull designers.

We do recommend though to take advantage of PatternFly variables as you build your styles. For example:

```less
.my-component {
  font-size: @font-size-sm;
  color: @color-pf-blue-100;
}
```

## Enjoy!
