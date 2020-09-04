Infos
-----

This project concerns the React Component automatic CLI generation topic: speeding up React Components creation/scaffolding with automatic CLI tools.

In particular, it demoes the use of a specific CLI tool:  
```
generate-react-cli
```

create-component npm script
---------------------------

We added a 'create-component' npm script, which is a wrapper to generate-react-cli.

Samples (npm run create-component)
----------------------------------

Create Hello Component
```
> COMPONENT=Hello npm run create-component
```

Create Hello Component with a customized param (withTest, in this case)
```
> COMPONENT=Hello npm run create-component -- --withTest=false
```

Create Home Component of type 'page' (assumes 'page' component in confguration)
```
> COMPONENT=Home npm run create-component -- --type=page
```

Create OneColumn Component of type 'layout' (assumes 'layout' component in confguration)
```
> COMPONENT=OneColumn npm run create-component -- --type=layout
```

generate-react-cli - Resources
------------------------------

[generate-react-cli npm module](https://www.npmjs.com/package/generate-react-cli)  
[generate-react-cli github repository](https://github.com/arminbro/generate-react-cli)

generate-react-cli - Configuration
----------------------------------

On its first use per project, generate-react-cli  will generate a generate-react-cli.json configuration file, which it will use on every following use.

generate-react-cli - Use cases
------------------------------

Default
```
> npx generate-react-cli component Box
```

Use with command line params (overrides config file)
```
> npx generate-react-cli component Box --withTest=false
```

Use with custom component type
```
> npx generate-react-cli component HomePage --type=page
```

generate-react-cli - Custom component types
-------------------------------------------

By default, GRC will use the component.default configuration rules when running the component command out of the box.  

What if you wanted to generate other types of components that have their own set of config rules (e.g., page or layout)?  

You can do so by extending the generate-react-cli.json config file like this.

```
{
  "usesTypeScript": false,
  "usesCssModule": true,
  "cssPreprocessor": "scss",
  "testLibrary": "Testing Library",
  "component": {
    "default": {
      "path": "src/components",
      "withLazy": false,
      "withStory": false,
      "withStyle": true,
      "withTest": true
    },
    "page": {
      "path": "src/pages",
      "withLazy": true,
      "withStory": false,
      "withStyle": true,
      "withTest": true
    },
    "layout": {
      "path": "src/layout",
      "withLazy": false,
      "withStory": false,
      "withStyle": false,
      "withTest": true
    }
  }
}
```

Now you can generate a component with your custom component types like this:

```
> npx generate-react-cli component HomePage --type=page
> npx generate-react-cli component BoxLayout --type=layout
```


