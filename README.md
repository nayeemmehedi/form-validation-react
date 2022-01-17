### form-validation-react

import React, { useEffect, useState } from 'react'

export default function Login() {

    const [form, setForm] = useState({
        name:"",
        password:""
    })

    const [formerror, setFormerror] = useState({})
    const [isSubmit, setisSubmit] = useState(false)





    const newvalue =(e)=>{

        const makevalue = {...form}
       
        makevalue[e.target.name] =e.target.value
        setForm(makevalue)

    }

    

    const onSubmit = (e) =>{
        
        e.preventDefault()
        setFormerror(validate(form))
        setisSubmit(true)


    }


    const validate =(v)=>{
       let  error ={}

        if(!v.name){
            error.name ="value not found.."

        }
        if(!v.password){
            error.password ="password not found.."

        }
        return error

    }

    useEffect(() => {
        if(Object.keys(formerror) == 0 && isSubmit){
            console.log(form)
        }
        
    }, [form,formerror,isSubmit])

    


    return (

        <form onSubmit={onSubmit}>
            <label htmlFor="">User Name</label>
           <input type="text" name="name" onChange ={newvalue} /> <br />
           <small style={{color:"red"}}>{formerror.name}</small><br />

           <label htmlFor="">Password</label>
           <input type="text" name="password" onChange ={newvalue}/> <br />
           <small style={{color:"red"}}>{formerror.password}</small><br />

           <input type="submit"  />

        </form>
    )
}
