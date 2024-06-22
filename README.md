# Deep-Copying-Method
For deep copying, where you need to ensure that all levels of nested objects are copied

you can use libraries "lodash" which provide a convenient cloneDeep function. Alternatively, you can manually create deep copies, but using a library is often simpler.

Using lodash for Deep Copy;

  First, install lodash if you haven't already:
  
     ===> "npm install lodash"
     
  Then, you can use the cloneDeep function to create deep copies of objects.


Here's an example of using lodash's cloneDeep to handle form state updates in a React component;

  
    import React, { useState, useEffect } from 'react';
    
    import { cloneDeep } from 'lodash';
    
    
    const initialForm = {
      [EMAIL_KEY]: '',
      [PASSWORD_KEY]: '',
      nestedField: {
        subField1: '',
        subField2: '',
      }
    };
    
    export default function Login() {
      const [form, setForm] = useState({
        ...initialForm,
        [EMAIL_KEY]: localStorage.getItem(EMAIL_KEY) || '',
      });
  
    
  
    const handleChange = (event) => {
      const { name, value, type } = event.target;
      const newValue = type === 'checkbox' ? event.target.checked : value;
  
      setForm((prevState) => {
        const updatedForm = cloneDeep(prevState);
        updatedForm[name] = newValue;
        return updatedForm;
      });
    };
  
    const handleNestedChange = (event) => {
      const { name, value } = event.target;
      setForm((prevState) => {
        const updatedForm = cloneDeep(prevState);
        updatedForm.nestedField[name] = value;
        return updatedForm;
      });
    };
  
   
