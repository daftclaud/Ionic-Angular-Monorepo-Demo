# Steps to create a monorepo with Angular/Ionic & Appflow
  1. Create an empty Angular workspace
      1. https://angular.io/guide/file-structure#multiple-projects
      2. ng new --create-application=false <project name>
  2. Initialize monorepo as a multi-app project
      1. https://ionicframework.com/docs/cli/configuration#multi-app-projects
      2. ionic init --multi-app
  3. Generate an application (I'll call mine mobile-client for this example)
      1. ng generate application --prefix=app mobile-client
      2. change outputPath in angular.json to ‘projects/mobile-client/www’
  4. Add Ionic to app
      1. https://ionicframework.com/docs/intro/cdn#ionic-angular
      2. ng add @ionic/angular --project=mobile-client
  5. Initialize Ionic app and make it default
      1. https://ionicframework.com/docs/cli/commands/init
      2. cd projects/mobile-client
      3. ionic init --type=angular --default
      4. cd ../..
  6. Add capacitor
      1. https://capacitorjs.com/solution/angular
      2. ng add @capacitor/angular --project=mobile-client
      3. move capacitor.config.json to project folder
      4. add “capacitor”: {} to “integrations” in ionic.config.json
  7. Add appflow.config.json
      1. https://ionic.io/docs/appflow/cookbook/appflow-config#overview
      2. "appId": <your Appflow appId>,
      3. "root": "projects/mobile-client",
      4. "dependencyInstallCommand": "cd ../.. && npm install",
      5. "webBuildCommand": "cd ../.. && npm run build"
  8. Push project to a repo and link project on Appflow!
