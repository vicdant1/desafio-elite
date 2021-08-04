<template>
    <div>
         <b-card
            :title="nome"
            :img-src="img"
            img-alt="Empresa"
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2 inactive"
            :class="[{'active': statusEmpresa}]"
            text-variant="white"
        >

            <b-card-text>
                Código: {{codigo}} <br/>
                Razão Social: {{razaoSocial}} <br/>
                Email: {{email}}
            </b-card-text>

            <div>
                <b-button v-b-modal="codigo" class="transition-2 btn-light">Ver detalhes</b-button>
                <b-modal :id="codigo" title="bootstrap vue" hide-footer>
                    <template #modal-title>
                        {{nome}} - #{{codigo}}
                    </template>
                    <div>
                        CNPJ: {{cnpj}}<br/>
                        Inscrição municipal: {{inscricaoMunicipal}}<br/>
                        Data de inclusão: {{dataInclusao}}<br/>
                        Responsável legal: {{responsavelLegal}}<br/>
                        Telefone para contato: {{telefoneContato}}
                    </div>

                    <div class="mt-4 modal-footer pb-0">
                        <b-button class="transition-2 btn-success">Exportar .xls</b-button>
                    </div>
                </b-modal>
            </div>
            
        </b-card>

    </div>
</template>

<script>
export default {
    name: 'CardEmpresa',
    props: ['nome', 'codigo', 'cnpj', 'razaoSocial', 'inscricaoMunicipal', 'dataInclusao', 'statusEmpresa', 'responsavelLegal', 'email', 'telefoneContato', 'img'],
}
</script>

<style scoped>
.inactive{
    background-color: #dc3545;
}

.active{
    background-color: rgb(23, 63, 182);
}

img{
    width: 318px;
    height: 191px;
}
</style>