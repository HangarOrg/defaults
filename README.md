# Hangar Engineering Defaults

> Chasing the best tool for the job is a particularly insidious trap when it comes to making progress—especially at the beginning of a project. We consider the relentless search for the best tool to be an optimization fallacy—in the same category as any other premature optimization.
>
> Searching for the optimal option is almost always expensive. Any belief that we can easily discover the best option by exhaustively testing each one is delusional. To make matters worse, we developers tend to enjoy tinkering with new technology and figuring out how things work, and this only amplifies the vicious cycle of such a pursuit.
>
> Instead of searching for the best option, we recommend a technique we call the default heuristic. The premise of this heuristic is that when the cost of acquiring new information is high and the consequence of deviating from a default choice is low, sticking with the default will likely be the optimal choice.
>
> — [Daniel Vasallo & Josh Pschorr, The Good Parts of AWS](https://gumroad.com/l/aws-good-parts)

This is precisely the situation Hangar’s companies find themselves in: we’re trying to execute in a difficult environment (the public sector), and we want to prioritize time to market. Thus, the cost of learning new technology is high — it delays that time to market — while the consequences of “using what we know” is low — we have sufficient experience to show that our default choices work just fine for our market.

Of course, portcos can and will differ — we expect the final call on everything will be made by each portfolio company. But here’s where we’ll start, and what we’ll use unless we find compelling reasons otherwise.

----

* Backend:
  * Language: Python 3.7+
  * Framework: Django
* Configuration Management: Ansible
* Cloud Provider: AWS (but carefully consider GCP for more compliance-heavy situations)
  * Default AWS Services:
    * Compute: Lambda, Fargate, EC2 (preferred in that order)
    * AI/ML: EMR + PySpark
    * Storage: S3
    * Database: RDS (Postgres), DynamoDB
    * Queue: SQS
    * Streaming Data: Kinesis
    * Logging and Monitoring: CloudWatch, CloudTrail
  * Default GCP Services: TBD
* DNS/Proxy: Cloudflare
* Databases:
  * Postgres for nearly everything, except...
  * Redis in some specific cases: fast K/V storage; caching; job queues.
  * Some exceptions on bigger AWS builds, see above.
* Deployment:
  * Heroku until it won’t work.
  * AWS Fargate after that.
  * Raw EC2 if nothing else works.
* Frontend:
  * HTML5
  * CSS via SCSS: [Hangar Style Kit](https://github.com/HangarOrg/hangar-style-kit)
  * JavaScript:
    * Use ES6 with Babel to compile to ES6 for the browser
    * Client side application with:
      * [React](https://reactjs.org/) for the template/view layer
      * [Redux](https://redux.js.org/) for managing data
      * More details about front-end conventions [here](./JS.md).
    * Authentication is on the server, via a cookie
  * Asset management: Parcel
* GIS:
  * Database: PostGIS
  * Backend framework: Django
  * Slippy maps: OpenLayers
  * Data format: GeoJSON
* Infrastructure Management: Terraform
* Job queue:
  * Celery + Redis
  * arteria/django-background-tasks for prototypes/demos, where the added cost/complexity of a real job queue isn’t worth the effort.
* Search:
  * Postgres full-text for commodity search
  * Elasticsearch where search is a core component, or where Postgres fails
* Metrics:
  * [Grafana](https://grafana.com/grafana/)
  * [Prometheus](https://grafana.com/oss/prometheus/)
* Paging:
  * [PagerDuty](https://www.pagerduty.com/)
* Error Tracking:
  * [Sentry](https://sentry.io/welcome/)
