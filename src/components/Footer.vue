<template>
    <footer class="container">
        <div class="row social">
            <div class="col-12">
                <i class="fa-brands fa-facebook-f"></i>
                <i class="fa-brands fa-instagram"></i>
                <i class="fa-brands fa-twitter"></i>
                <i class="fa-brands fa-youtube"></i>
            </div>
    </div>
    <div class="row lists">
        <div class="col-6 col-md-3">
            <ul>
                <li>Audiodescrizione</li>
                <li>Rapporti con gli investitori</li>
                <li>Note legali</li>
            </ul>
        </div>
        <div class="col-6 col-md-3">
            <ul>
                <li>Centro assistenza</li>
                <li>Opportunità di lavoro</li>
                <li>Preferenze per i cookie</li>
            </ul>
        </div>
        <div class="col-6 col-md-3">
            <ul>
                <li>Carte regalo</li>
                <li>Condizioni di utilizzo</li>
                <li>Informazioni sull'azienda</li>
            </ul>
        </div>
        <div class="col-6 col-md-3">
            <ul>
                <li>Media Center</li>
                <li>Privacy</li>
                <li>Contattaci</li>
            </ul>
        </div>
    </div>
    <div class="row buttons">
        <div class="col-12">
            <button class="btn">Codice di servizio</button>
        </div>
    </div>
    </footer>
</template>

<style lang="scss" scoped>
    footer {
        padding: 50px 0px;
        color: var(--grigio);

        .social, .lists, .buttons {
            padding: 15px;
        }
        
        .social {
            i {
            margin-right: 16px;
            font-size: 22px;
            }
        }

        .lists {
            li {
                padding-right: 5px;
                list-style: none;
                &:not(:last-child) {
                    margin-bottom: 10px;
                }
            }
        }

        .buttons {
            button.btn {
                color: var(--grigio);
                border: 1px solid var(--grigio);
            }
        }
    }
</style>
