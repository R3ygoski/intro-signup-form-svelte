<script>
  import Input from './Input.svelte'
  const nameRegex = new RegExp ('^[a-z]+$','i')

  let formInputs = {
    firstName: '',
    lastName: '',
    email: '',
    password: '',
  }
  let errorsInputs = {
    firstName: false,
    lastName: false,
    email: false,
    password: false,
  }
  let errorsDesc = {
    firstName: '',
    lastName: '',
    email: '',
    password: '',
  }

  function handleSubmit(e){
    e.preventDefault()
    if(validateForm()){
      formInputs.firstName = ''
      formInputs.lastName = ''
      formInputs.email = ''
      formInputs.password = ''
    }
  }

  function validateForm(){
    errorsInputs.firstName = firstNameValidator()
    errorsInputs.lastName = lastNameValidator()
    errorsInputs.email = emailValidator()
    errorsInputs.password = passwordValidator()
    return !errorsInputs.firstName && !errorsInputs.lastName && !errorsInputs.email && !errorsInputs.password
  }
 
  function firstNameValidator(){
    if (formInputs.firstName===''){
      errorsDesc.firstName="First Name cannot be Empty"
      return true
    } else if (!nameRegex.test(formInputs.firstName)){
      errorsDesc.firstName="First Name is Invalid"
      return true
    } else {
      return false
    }
  }
  function lastNameValidator(){
    if (formInputs.lastName===''){
      errorsDesc.lastName="Last Name cannot be Empty"
      return true
    } else if (!nameRegex.test(formInputs.lastName)){
      errorsDesc.lastName="Last Name is Invalid"
      return true
    } else {
      return false
    }
  }
  function emailValidator(){
    if (formInputs.email===''){
      errorsDesc.email="Email cannot be Empty"
      return true
    } else if (!formInputs.email.includes('@')){
      errorsDesc.email="Email must have '@' "
      return true
    } else if (!formInputs.email.includes('.com')){
      errorsDesc.email="Email must have '.com'"
      return true
    } else {
      return false
    }
  }
  function passwordValidator(){
    if (formInputs.password===''){
      errorsDesc.password="Password cannot be Empty"
      return true
    } else if (formInputs.password.length < 8){
      errorsDesc.password="Password too short"
      return true
    } else {
      return false
    }
  }
</script>

<form on:submit={(e)=>{handleSubmit(e)}} class="form">
  <Input
    bind:value={formInputs.firstName}
    type="text"
    placeholder="First Name"
    error={errorsInputs.firstName}
    errorDesc={errorsDesc.firstName}
    />
  <Input 
    bind:value={formInputs.lastName}
    type="text"
    placeholder="Last Name"
    error={errorsInputs.lastName}
    errorDesc={errorsDesc.lastName}
    />
  <Input 
    bind:value={formInputs.email}
    type="email"
    placeholder="Email Address"
    error={errorsInputs.email}
    errorDesc={errorsDesc.email}
    />
  <Input 
    bind:value={formInputs.password}
    type="password"
    placeholder="Password"
    error={errorsInputs.password}
    errorDesc={errorsDesc.password}
    />
  <button type="submit">
    Claim your free trial
  </button>

  <p>By clicking the button, you are agreeing to our 
    <span>Terms and Services</span>
  </p>
</form>

<style lang="scss">
  @use '../scss/var';
  .form {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    padding: 1.4rem 0;
    margin-top: 1.5rem;
    background: var.$white;
    min-height: 440px;
    border-radius: .5rem;
    min-width: 315px;
    button {
      height: 56px;
      width: 280px;
      background: var.$green;
      text-transform: uppercase;
      color: var.$white;
      border: none;
      border-radius: .4rem;
      box-shadow: 0 -4px 0 inset rgba(0,0,0,.2);
      font-size: 1rem;
      cursor: pointer;
      &:hover {
        filter: grayscale(.3);
      }
    }
    p {
      margin-top: .5rem;
      text-align: center;
      font-size: .7rem;
      width: 75%;
      color: var.$grayishBlue;
      span {
        color: var.$red;
        font-weight: 600;
        cursor: pointer;
      }
    }
  }
  @media (min-width: 1024px){
    .form {
      button {
        width: 460px;
      }
    }
  }
</style>