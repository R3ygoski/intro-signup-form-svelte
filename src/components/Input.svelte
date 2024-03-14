<script>
    export let placeholder
    export let type
    export let value
    export let error
    export let errorDesc
</script>

<div class="input_container">
    {#if type === 'text'}
    <input bind:value type="text"placeholder={placeholder} class="input" class:input_error={error===true} />
    
    {:else if type === 'email'}
    <input bind:value type="email"placeholder={placeholder} class="input" class:input_error={error===true} />
    
    {:else if type === 'password'}
    <input bind:value type="password"placeholder={placeholder} class="input" class:input_error={error===true} />

    {/if}

    {#if error === true}
        <p class="desc_error">{errorDesc}</p>
        <div class="icon_error"></div>
    {/if}
</div>

<style lang="scss">
    @use '../scss/var';
    .input_container {
        display: flex;
        flex-direction: column;
        align-items: flex-end;
        position: relative;
        .input {
            height: 56px;
            min-width: 280px;
            padding: 0 1.2rem;
            border-radius: .4rem;
            border: 1px solid var.$grayishBlue;
            color: var.$darkBlue; 
            font-weight: 600;
            &::placeholder {
               color: var.$darkBlue; 
               filter: contrast(50%);
               font-weight: 600;
            }
            &:focus {
                outline: 1px solid var.$blue;
                outline-offset: -1px;
            }
        }
        .input_error {
            outline: 1px solid var.$red;
            color: var.$red;
            outline-offset: -1px;
        }
        .icon_error {
            width: 24px;
            height: 24px;
            position: absolute;
            top: 15px;
            right: 14px;
            background-image: url(./assets/icon-error.svg);
            background-repeat: no-repeat;
            background-position: right;
            background-size: contain;
        }
        .desc_error {
            color: var.$red;
            font-size: .75rem;
            margin-bottom: .5rem;
        }
    }
    @media (min-width: 768px){
        .input_container {
            .input {
                width: 420px;
            }
        }
    }
    @media (min-width: 1024px){
        .input_container {
            .input {
                width: 460px;
            }
        }
    }
</style>