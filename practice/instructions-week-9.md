## Instalation
1. Install a new vite project.

## Creating the 'Gallery' Component
1. Create a new file called Gallery.vue in the components directory
2. Add the template section to the file. Start with a root div element and assign an id attribute set to "gallery". Also, give it a class of "gallery"
```
<div id="gallery" class="gallery">
  
</div>
```

3. Define the prop 'items' using the shorthand syntax ['items']. This means that the Gallery component expects a prop named items.
```
<script>

</script>
```

4. Inside the div#gallery element, use the v-for directive to iterate over each item in the items array. 
```
<div class="gallery-item" >
  
</div>
```
5. Within the div element, add an img element with a class of "gallery-item-image" and set the src attribute.
```
<img class="gallery-item-image" src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png" />
```

6. Add an h2 element with a class of "gallery-item-name" and bind its text content to item.name
```
<h2 class="gallery-item-name"> </h2>
```

## Create the App component

1. Inside the App.vue template, add a div with a class of "gallery-title" and a h1 element. Set the text content to "Pokemon Gallery"
```
<template>
  <div class="gallery-title">
    <h1>Pokemon Gallery</h1>
  </div> 
</template>
```
2. Below the div element, add the Gallery component. Use the Gallery component tag and self-closing syntax.
```
<Gallery />
```

4. Import the Gallery component at the top of the script section. Use the import statement and specify the relative path to the Gallery component file.
```
<script>

</script>
```
5. Register the Gallery component in the components section of the export default object.
```
export default {
  components: {Gallery}
}
```
6. Import the pokedex and use it to initialize a reactive variable (inside the data function). 
```
import pokedex from "./utils/pokedex"
```

7. Bind the value of the pokemons data property to the 'items' prop of the Gallery component.
```
<Gallery :items="items"/>
```



## Event handling

1. Use the @click directive to listen for a click event on the element.
```
@click=""
```

2. When the element is clicked, call the toggleCaught method and pass the item as an argument.
```
@click="toggleCaught(item)"
```

3. Inside the toggleCaught method, define the emit event toggle-caught and send the item to the parent 
```
methods: {
 
}
```

4. In the parent component, listen for the emitted event. Specify the event name @toggle-caught and provide the method 'updateCaughtStatus' to handle the event.

``` 
@toggle-caught="updateCaughtStatus"
```
```
updateCaughtStatus(updatedItem) {
  this.items = this.items.map(item => item.id === updatedItem.id ? {...item, caught: !item.caught} : item)
},
```

5. In the child component, use the :class directive to apply different styles to the clicked element based on the value of item.caught 
```
:class="item.caught ? 'gallery-item caught' : 'gallery-item'"
```


//Continue here...

## Form handling
1. In the parent, create the newItem reactive data and set the default values for id, name, caught
```
newItem: {
            id: null,
            name: '',
            caught: false
        }
```

2. Create a form,  listen to the submit event and prevent the default behavior. Call the 'addItem' method
```
<form>
</form>
```

4. Inside the form create a input element and a submit button. Use the two-way data binding to bind the input value with the newItem.name property
```
<input type="text" placeholder="Name">
<button type="submit">Add Item</button>
```

3. Define the 'addItem' method
```
methods: {
        addItem() { }
}
```
4. Inside the method, generate a unique ID for the new item
```
const newId = this.items.length +1
```

5. Set the ID and add the new item to the items array
```
this.newItem.id = newId
this.items.push(this.newItem)
```

6. Clear the form fields for the next input
```
this.newItem = {
            id: null,
            name: '',
            caught: false
            }
```

7. Store the 'items' array in the browser's localStorage as a JSON string.
```

localStorage.setItem('items', JSON.stringify(this.items));
      
```


## Lifecycle hook
1. Retrieve items from localStorage when the component is created
```
created() {
  const storedItems = localStorage.getItem('items');
  if (storedItems) {
  this.items = JSON.parse(storedItems);
  }
}
```



