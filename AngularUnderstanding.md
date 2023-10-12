# Understanding Angular



## [Creating components ](https://angular.io/guide/component-overview)

- Component = (1 html, 2 ts, 3: css?)
- To create a component, one must have an Angular workspace and CLI
- Best way to create is using the angular CLI
	- ng generate component <component-name>
	- This will create a directory containing CSS, TS, HTML, .spec.ts (test file)
	- If we were to do it manually it would comprise of 
		- Create a new file, <component-name>.component.ts.
		- add import { Component } from '@angular/core';
		-  add a @Component({ }) decorator
		-  add CSS selector
		- Define the HTML template
		- Define Styles 
		- Add export class ComponentOverviewComponent { }



- selector allows your component to be accessed extenally with the specified 'selector-id'
- You can directly add a template using template: or you can use the preferred templateUrl: property. templateUrl is better as files grow larger and to separate template and component in a clean manner
- You can NOT use both template and templateUrl at the same time
- You can specify a components styling using styleUrls property. You can also use host and bootstrap-esque css frameworks
- You can also add in stlye CSS directly using styles

## [Life cycles](https://angular.io/guide/lifecycle-hooks)

	- 	 each instance of a component has a life cycle. 
	-	 Starting when the component is rendered (with child views)
	-	 Angular updates the component instance using change detection. Data bound properties are updated when new ones come along, and change detection is used for this purpose
	-	 NB do not use functions in the template because it triggers change detection -> degraded performance
	-	 The lifecycle ends when angular destroys that component instance. It is at this time removed from the DOM
	-	 The same applies for directives (contains selector)
	-	 

	
## [View encapsulation](https://angular.io/guide/view-encapsulation)	
	- How views are encapsulated
	- A view is the html 
	- thing you see
	
	
##  [Componet interaction](https://angular.io/guide/component-interaction)	
	
	- Talks about how to pass data to child-parent 
	- How to pass to parent-child
	- You can use setters and or the ngOnInit life cycle
	- We also have eventSmitters 
	- Finally there is the @ViewChild decorator



## [Component styles](https://angular.io/guide/component-styles)
	
	
	- Styles refers to the css stuff
	- how you make it look

	

## [sharing data](https://angular.io/guide/inputs-outputs)


- More on input output 
- More on property binding in the html
	
	
	
	
## [Content projection](https://angular.io/guide/content-projection)
	
	
	-  Using html elements such as ngIf, ngTemplate etc 
- [load dynamically](https://angular.io/guide/content-projection)
	
	
## [Angular elements](https://angular.io/guide/content-projection)
	
	- Gives extra capability to your component
	- Gives the browser more ability
	- Interact with APIs
	- Custom elements
	- Browser support
	- Mappling



# [Angular Templates](https://angular.io/guide/template-overview)

	- Property binding
	- Attr binding
	- interpolation
	- class and style binding 
	- event binding 
	- input output 
	- directives
	
	
	- events are "()"
	- (click)="deleteHero()"

 
## [Binding](https://angular.io/guide/binding-overview) 

- binding creates a connection used to synchronise data
- angular does this using its built in change detection 
- reference values such as "#customerInput" 

- attr binding 
- prop binding 
- class and style binding
- event binding 
- 2 way binding 

## [Pipes](https://angular.io/guide/pipes-overview) 

- The pipe operator has a higher precedence than the ternary operator (?:), which means a ? b : c | x is parsed as a ? b : (c | x)
- Built-in pipes
- custom pipes


## [Template Ref Values ](https://angular.io/guide/template-reference-variables)

- Template variables help you use data from one part of a template in another part of the template. Use template variables to perform tasks such as respond to user input or finely tune your application's forms
- Can be used with ngForm
- Svg as template


## [Directives](https://angular.io/guide/built-in-directives)

-	Directives are classes that add additional behavior to elements in your Angular applications. Use Angular's built-in directives to manage forms, lists, styles, and what users see.

- Component is a directive
- NgClass	Adds and removes a set of CSS classes
- NgStyle	Adds and removes a set of HTML styles
- NgModel	Adds two-way data binding to an HTML form element
- ngSwitch, ngIf, ngFor, etc.... are all directives

- [attr directive](https://angular.io/guide/attribute-directives)
- [structural directives](https://angular.io/guide/structural-directives)
- 	1 directive per element


- Can add input output to componenet API in directive



## [Dependency injection ](https://angular.io/guide/dependency-injection-overview)
- Dependency Injection, or DI, is a design pattern and mechanism for creating and delivering some parts of an application to other parts of an application that require them.
- increase flexibility and modularity
- In Angular, dependencies are typically services
- Providing dependency "@Injectable()
class HeroService {}"
- When you register a provider at the component level, you get a new instance of the service with each new instance of that component
- At the application root level, which allows injecting it into other classes in the application. This can be done by adding the providedIn: 'root' field to the @Injectable decorator:
- [Hierarchies for injectors](https://angular.io/guide/hierarchical-dependency-injection)


# [Dev Guide](https://angular.io/guide/developer-guide-overview)
- Standalone components 
- Lazy loading is the practice of delaying load or initialization of resources or objects until they're actually needed to improve performance and save system resources
- loadChildren lazy loads many routes at once
- Migrating to standalone components

## [Change detection](https://angular.io/guide/change-detection)
	-  Angular dev tools (use)
	-  "Profiler" -> we can see how long we spent on each change detection per component!
	-  Prevent redundent change detection being triggered
	-  Events bypass onPush !
	-  A renders B, but not all of B needs to be re-rendered
	-  We then break B down in to C and D
	-  Now A renders C and D
	-  This increases performance as only D needs re-render and C not!
-  [	Types of change detection](https://angular.io/guide/change-detection-skipping-subtrees)



## [Routing](https://angular.io/guide/routing-overview#angular-routing)
-	In a single-page app, you change what the user sees by showing or hiding portions of the display that correspond to particular components, rather than going out to the server to get a new page
- Routing strategies 
- Path types
- Registering a path
- sub routes


## [Forms](https://angular.io/guide/forms-overview#introduction-to-forms-in-angular)
- Forms handle user input NB
- buolding forms
- dynamic forms


## [HTTP comms](https://angular.io/guide/http-setup-server-communication)

- Before you can use HttpClient, you need to import the Angular HttpClientModule. Most apps do so in the root AppModule.

- You can then inject the HttpClient service as a dependency of an application class
- @Injectable()
export class ConfigService {
  constructor(private http: HttpClient) { }
}
- how to set up server communication and request data 
- Get()
- make JSON request
- error handling
- post requests
- config urls
- Interceptors can be used for caching etc
- Pass metadata to interceptors
- debounce for optimisation
- XSS protection
- tests
- Hydration improves application performance by avoiding extra work to re-create DOM nodes.
- Without hydration enabled, server side rendered Angular applications will destroy and re-render the application's DOM, which may result in a visible UI flicker


## Security
- To block XSS attacks, you must prevent malicious code from entering the Document Object Model (DOM). 
- To prevent these vulnerabilities, always use the default Ahead-Of-Time (AOT) template compiler in production deployments
- Angular sanitzation
- DomSanitizer
- Content security policy
- Server-side XSS protection
- Using AOT compiler 
- Cross-site request forgery (an attacker tricks the user into visiting a different web page (such as evil.com) with malignant code)
- Cross-site script inclusion (XSSI) ( JSON vulnerability)
- This attack is only successful if the returned JSON is executable as JavaScript. Servers can prevent an attack by prefixing all JSON responses to make them non-executable, by convention, using the well-known string ")]}',\n"
- Angular's HttpClient library recognizes this convention and automatically strips the string ")]}',\n" from all responses before further parsing






#[ Best Practice](https://angular.io/guide/security)

## Property Binsing
- Avoid side effects
- To lazy load Angular modules, use loadChildren (instead of component) in your AppRoutingModule routes configuration as follows


## Lazy loading 
- Lazy loading is done for routing in this example 
	
		- const routes: Routes = [
		  {
		    path: 'items',
		    loadChildren: () => import('./items/items.module').then(m => m.ItemsModule)
		  }
		]; 




# [Angular Tools](https://angular.io/guide/cli-builder)
	
- 
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	 
