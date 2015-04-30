Yadda HTML Report
=================

**INSTALLATION**

      npm install yadda-html-reporter


** USAGE**

In order to use the yadda html report you need to do the following:

a. instantiate YaddaReport:

		var YaddaHtml = require('yadda-html-reporter');
		var YaddaHtmlRep = new YaddaHtml(reportsOutputLocation);

b. your Yadda.FeatureFileSearch section should look like this:

new Yadda.FeatureFileSearch(featuresLocation).each(function (file) {


        featureFile(file, function (feature) {
            YaddaHtmlRep.onFeature(feature);  // First statement

            before(function (done) {
                YaddaHtmlRep.onBefore(); // Second
                
                context = {
                    // something usually goes here
                };
                done();
            });

            beforeEach(function () {
                YaddaHtmlRep.onBeforeEach();
            });


            var yadda = new Yadda.Yadda(library, context);
            scenarios(feature.scenarios, function (scenario) {
                steps(scenario.steps, function (step, done) {
                    YaddaHtmlRep.onStep(scenario);
                    yadda.run(step, context, done);
                });
            });

            afterEach(function () {
                YaddaHtmlRep.onAfterEach(this.currentTest);
            });

            after(function (done) {
                YaddaHtmlRep.onAfter();
                    done();
            });

        });
    });





