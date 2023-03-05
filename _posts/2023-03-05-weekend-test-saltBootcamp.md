---
layout: post
title: "Note: Weekend Test saltBootcamp"
date: 2023-03-05 23:00:00 +0200
categories: Note Salt
---

## 1. How to submit information in a form

It is different from vanila html that uses submit to get all the information.

You should add `onChange={onChangehandleFunction}` in each `<input>` element to get the data.

And preferablely store the data in `state`.

Eventually in the `<form>` element, you add `onSubmit={submitHandleFunction}` to handle the action of submit. Usually it is to send data to other places.

## 2. How to send data to child component?

## 3. How to send data to parent component?

By callback function! Send a callback function to child component.

## 4. Example of using `axios` to send a post request

```ts
const newDeveloper = {a:1,b:'yes'}
try {
      const postResponse = await axios.post('http://localhost:3001/developers', newDeveloper)
      console.log(postResponse.data)
    } catch (error) {
      console.log(error)
    }
```

## 5. Example of using `fetch` in `.tsx` code

The fetching triggered by both the changing of state `updateData` in this component and `updateDataIn` from parent component.

```ts

// Define the fetching function from outside first
const fetchingDevs = async (url: string) => {
  const result = await fetch('http://localhost:3001/'+ url).then(response => response.json())
  return result
}


const RenderBootCamp = ( {bootcampDisplay, updateDataIn} : RenderBootCampProps) => {
  const [data, setData] = useState<Developer[] | null>(null);
  const [updateData, setUpdateData] = useState<number>(0)

  const updateDataFunction = () => {
    setUpdateData(updateData + 1)
  }

  useEffect(() => {
    fetchingDevs('developers').then(result => setData(result.developers))
   },[]);

  useEffect(() => {
    fetchingDevs('developers').then(result => setData(result.developers))
   },[updateData, updateDataIn]); 

  // pass the data to child component for rendering
  return (
      <div className="gallery">
        <RenderDevelopers bootcampName={bootcampDisplay} developers={data} bootcamps={bootcamps} instructors={instructors} update={updateDataFunction}/>
      </div>
  )
}
```

## 6. All kinds of `event`

### 1. ChangeEvent

### 2. FormEvent