<footer>
    <p class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
      Coded by <a href="https://github.com/R3ygoski">Bernardo Poggioni</a>.
    </p>
</footer>

<style lang="scss">
    @use '../scss/var';
    footer {
        text-align: center;
        position: absolute;
        bottom: 0;
        p {
            font-size: 14px;
            a {
                font-size: 14px;
                color: var.$veryDarkBlue;
            }
        }
    }
    @media (min-width: 1024px){
        footer {
            position: absolute;
            bottom: -10%;
            left: 0;
            right: 0;
        }
    }
</style>