# Sitecore YAML - MCP Server

## Files
### components.yaml
Used to define all components and their caracteristics. 
* Name: This is the display name of the components, the components name is used in code by removing all white spaces from its name. For instance, Rich Text becomes RichText.tsx.
* Category: The component category is often used as a logical distiction among the components and to organize them in different folders.
* Fields: Sitecore Fields available in the components. When there are no fields present, means the component doesn't need a data source.

The components files are organized in folders, for instance, a component with Name "Title" and Category "Page Structure" is created in a folder "/components/page-structure/Title.tsx".

All placeholder names should have no dashes. A component called "One Column Container" should use a placeholder key:
 ``phKey = `container-${props?.params?.DynamicPlaceholderId}`; ``

### pagetypes.yaml
Page types YAML is used to define what pages can be created. They are mapped in Sitecore with templates. Each page type becomes a template.
Also each page type will generate a container component organized under a folder called "Page Types Components". A container component is a component with only a Sitecore placeholder.

### hierarchy.yaml
Always use this file to determine when to add a <placeholder> in the component .tsx.
All components that are present and have other components nested into them, must have a placeholder in the next.js .tsx compoent file
Example
hierarchy:
  components:
    One Column: 
      - Title
      - Other component

In the example, the OneColumn.tsx must have a <placeholder> and the Title.tsx and OtherComponent.tsx not necessarily (unless they also nest components).