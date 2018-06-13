# Marine Plastics Monitor API
### Sponsored by [Clean Oceans International](https://cleanoceansinternational.org/)
### Live site: https://marineplasticsDB.herokuapp.com/api

An API built for the [Marine Plastics Monitor Site](https://marineplastics.herokuapp.com).

## Getting Started

### Prerequesites
Need access to our accounts on (need to contact one of the developers)
  * Heroku
  * MLab

Code for the site is here: https://github.com/vincentwu96/MarinePlastics

### Installing
1. Clone the repo: `git clone https://github.com/vincentwu96/MarinePlasticsDB.git`
2. Install the dependencies: `npm install`
3. Run the development environment: `npm run start`

### Deploying
To deploy to the live site: https://devcenter.heroku.com/articles/git
  1. Sign into Heroku in terminal
  2. Add a remote to the existing Heroku site
  3. Deploy with `git push heroku master`
If the site breaks, view the logs on Heroku for an error

### Quirks
In `./server.js`, for both `router.route('/comments')` and `router.route('/comments/:id').put()` there is the following check: 
```
  (req.body.user) ? comment.user = req.body.user : null;
  (req.body.email) ? comment.email = req.body.email : null;
  (req.body.input_date) ? comment.input_date = req.body.input_date : null;
  (req.body.org) ? comment.org = req.body.org : null;
  (req.body.date) ? comment.date = req.body.date : null;
  (req.body.beach) ? comment.beach = req.body.beach : null;
  (req.body.reason) ? comment.reason = req.body.reason : null;
  (req.body.st) ? comment.st = req.body.st : null;
  (req.body.lat) ? comment.lat = req.body.lat : null;
  (req.body.lon) ? comment.lon = req.body.lon : null;
  (req.body.slope) ? comment.slope = req.body.slope : null;
  (req.body.nroName) ? comment.nroName = req.body.nroName : null;
  (req.body.nroDist) ? comment.nroDist = req.body.nroDist : null;
  (req.body.aspect) ? comment.aspect = req.body.aspect : null;
  (req.body.lastTide) ? comment.lastTide = req.body.lastTide : null;
  (req.body.nextTide) ? comment.nextTide = req.body.nextTide : null;
  (req.body.windDir) ? comment.windDir = req.body.windDir : null;
  (req.body.majorUse) ? comment.majorUse = req.body.majorUse : null;
  (req.body.weight) ? comment.weight = req.body.weight : null;
  (req.body.NumberOfPeople) ? comment.NumberOfPeople = req.body.NumberOfPeople : null;
  (req.body.SRSData) ? comment.SRSData = req.body.SRSData : null;
  (req.body.SRSTotal) ? comment.SRSTotal = req.body.SRSTotal : null;
  (req.body.ASData) ? comment.ASData = req.body.ASData : null;
  (req.body.ASTotal) ? comment.ASTotal = req.body.ASTotal : null;
```

This shouldn't be necessary, there should be a way to loop through all the keys in `req.body` and `comment` instead. There was an effort to do this, but there wasn't time to make it work:

```
  for (const key in comment) {
    if (comment.hasOwnProperty(key)) {
      const val = req.body[key];
      if (val) comment[key] = val;
    }
  }
```

## Built With
* [MLab](https://www.mlab.com/)
* [Mongoose](http://mongoosejs.com/) - for setting up our database schemas
* [Heroku](http://heroku.com/)
* [Express](https://expressjs.com/)

## Product Backlog
There is a lot that we would still love to see happen:
  * Sorting on the API side as opposed to on the client side
    * i.e. be able to call a location to the api and have it return all entries from that place
  * Faster response (might just be because we are on a free MLab/Heroku plan)

## Developers:
* Guita Vahdatinia - gvahdati@ucsc.edu
* Kianna Mark - kjmark@ucsc.edu
* Michael Pluguez - mpluguez@ucsc.edu
* Megan Sharp - mesharp@ucsc.edu
* Lee White - lnwhite@ucsc.edu
* Vincent Wu - vwu5@ucsc.edu
