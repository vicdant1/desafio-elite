<template>
  <div>
    <!-- Filtro -->
    <div class="row d-flex justify-content-center mt-5 mb-5">
      <b-form inline>
        <b-form-input class="mr-3" placeholder="Pesquisa" v-model="search">
        </b-form-input>
        <b-form-select class="mr-3" v-model="select" :options="options">
        </b-form-select>
        <b-button class="transition-4 btn-success" title="Limpar filtro" v-b-tooltip.hover @click="limparFiltro">Limpar filtro</b-button>
        <b-button class="transition-4 btn-warning ml-2" @click="saveAsExcel()">Relatório Geral</b-button>
      </b-form>
    </div>

    <!-- Card Generate -->

    <div class="container d-flex flex-wrap justify-content-center">
      <div class="row" v-for="empresa in itemsFiltered" :key="empresa">
        <CardEmpresa class="mx-4" :nome="empresa.nome" :codigo="empresa.codigo" :cnpj="empresa.cnpj" :razaoSocial="empresa.razaoSocial" :inscricaoMunicipal="empresa.inscricaoMunicipal" :dataInclusao="empresa.dataInclusao" :statusEmpresa="empresa.statusEmpresa" :responsavelLegal="empresa.responsavelLegal" :email="empresa.email" :telefoneContato="empresa.telefoneContato" :img="empresa.img"  @generateExcel="initExcel($event)"/>
      </div>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.17.0/xlsx.min.js" integrity="sha512-WaHZ16+n6qSSVxDii8MZGmFlnro3iZdJa/hb1XKraoMx1/HVILhLdAX22ypk4lT/8+t4XMYcjzCDwfvZ1CAJgw==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
    <script src="../static/filesaver.js"></script>
  </div>
</template>

<script>

export default {

  data(){
    return{
      data: [
        {
          nome: 'Super Show Bis',
          codigo: '0',
          cnpj: '8.895.650/0001-54',
          razaoSocial: 'Comério de Alimentos',
          inscricaoMunicipal: '9340934',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Fátima Medeiros',
          email: 'supershow@supershowbis.com',
          telefoneContato: '(84) 3302-3354',
          img: 'https://i0.wp.com/blog.flaviomarinho.com.br/wp-content/uploads/2020/11/gewgew.jpg?w=810&ssl=1'
        },
        {
          nome: 'Zani madeiras LTDA.',
          codigo: '1',
          cnpj: '8.589.650/0001-84',
          razaoSocial: 'Madeireira',
          inscricaoMunicipal: '5151845',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Valdencir Soares',
          email: 'zani@zanimadeiras.com',
          telefoneContato: '(84) 3102-3954',
          img: 'https://www.zanimadeiras.com.br/assets/images/zanipb2-492x323.jpg'
        },
        {
          nome: 'Vicunha Têxtil S.A',
          codigo: '2',
          cnpj: '8.07332190000193/0001-54',
          razaoSocial: 'Vicunha Textil S/a.',
          inscricaoMunicipal: '4454151',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Marcelino Andrade',
          email: 'vicunhatextil@vicunha.com',
          telefoneContato: '(84) 3682-3954',
          img: 'https://www.operacionalsolution.com.br/wp-content/uploads/2017/12/VICUNHA-1.png'
        },
        {
          nome: 'JMT Service',
          codigo: '3',
          cnpj: '8.845.650/0001-74',
          razaoSocial: 'Prestação de serviços',
          inscricaoMunicipal: '5265284',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Rennan Nascimento',
          email: 'jmtservices@jmtservices.com',
          telefoneContato: '(84) 4782-9985',
          img: 'https://1.bp.blogspot.com/-xN2SCIYEqKA/Xpp7R0KsMdI/AAAAAAAAQDw/rhQJvpvfgEo02TgCmuQRSjbOB6hoYzNGgCLcBGAsYHQ/s1600/LOGO%2BJMT.png'
        },
        {
          nome: 'Drogasil',
          codigo: '4',
          cnpj: '8.884.625/0501-24',
          razaoSocial: 'Farmácia/drogaria',
          inscricaoMunicipal: '9340934',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Fátima Medeiros',
          email: 'drogasil@drogasil.com',
          telefoneContato: '(84) 3302-3354',
          img: 'https://upload.wikimedia.org/wikipedia/commons/7/77/Logo_drogasil.png'
        },
        {
          nome: 'Auri Autopeças',
          codigo: '5',
          cnpj: '8.815.234/2343-54',
          razaoSocial: 'Autopeças',
          inscricaoMunicipal: '532542',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Aureo Rocha',
          email: 'auri@auriatpcs.com',
          telefoneContato: '(84) 3633-5421',
          img: 'https://lh3.googleusercontent.com/proxy/3a67trhszzqM5uLgSbSP4k1gkFbrnp8AMif89f2mcLLDdc85agv2yd_yvheBC0tW7MG5o-5tpM_ikU9aVltMlAY8a6ILDLFFemCJfDE'
        },
        {
          nome: 'Adm. Arena das Dunas',
          codigo: '6',
          cnpj: '8.234.544/6543-13',
          razaoSocial: 'Admnistração de estádios',
          inscricaoMunicipal: '1526415',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Hiranilson Dantas',
          email: 'arena@arenadasdunas.com',
          telefoneContato: '(84) 6558-6445',
          img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/Natal%2C_Brazil_-_Arena_das_Dunas.jpg/280px-Natal%2C_Brazil_-_Arena_das_Dunas.jpg'
        },
        {
          nome: 'Moura Dubeux',
          codigo: '7',
          cnpj: '8.895.241/5154-54',
          razaoSocial: 'Construtora',
          inscricaoMunicipal: '126314',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Higor Dubeux',
          email: 'mdbr@dubeux.com',
          telefoneContato: '(84) 4234-5421',
          img: 'https://yt3.ggpht.com/ytc/AKedOLRlVoneqJB14f1ChCcyClPqP2ScYRqj7uDaMX_BAQ=s900-c-k-c0x00ffffff-no-rj'
        },
        {
          nome: 'Riachuelo',
          codigo: '8',
          cnpj: '8.895.234/2343-54',
          razaoSocial: 'Vestuário',
          inscricaoMunicipal: '532432',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Flávio Rocha',
          email: 'rchlo@riachuelo.com',
          telefoneContato: '(84) 3423-5421',
          img: 'https://veja.abril.com.br/wp-content/uploads/2020/06/Riachuelo-Fachada.jpg?quality=70&strip=info&w=656'
        },
        {
          'nome': 'Viação nordeste',
          'codigo': '9',
          'cnpj': '8.823.434/4341-54',
          'razaoSocial': 'Transporte',
          'inscricaoMunicipal': '565984',
          'dataInclusao': '',
          'statusEmpresa': 0,
          'responsavelLegal': 'Flávio Rocha',
          'email': 'viacao@nordeste.com',
          'telefoneContato': '(84) 5456-1251',
          'img': 'https://s2.glbimg.com/GZhacxriIbuGHPUAZJTzI7Slj9M=/0x258:1632x1224/984x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_59edd422c0c84a879bd37670ae4f538a/internal_photos/bs/2020/8/J/JwgdnORnCoQDkZvy5q1A/viacao-nordeste.jpeg'
        },
        {
          nome: 'Natal Computer',
          codigo: '10',
          cnpj: '8.895.234/3455-54',
          razaoSocial: 'Computação',
          inscricaoMunicipal: '432432',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'John Lennon',
          email: 'lennon@natalcomp.com',
          telefoneContato: '(84) 3333-1222',
          img: 'https://s3-us-west-2.amazonaws.com/media.linklist.bio/avatars/53fce54ea1c8e8ff6a52bbf0ac688461.png'
        },
        {
          nome: 'Zara LTDA',
          codigo: '11',
          cnpj: '8.895.999/2343-54',
          razaoSocial: 'Vestuário',
          inscricaoMunicipal: '123454',
          dataInclusao: '',
          statusEmpresa: 1,
          responsavelLegal: 'Paul McCartney',
          email: 'zara@zara.com',
          telefoneContato: '(84) 3242-1231',
          img: 'https://files.aredacao.com.br/upload/content/zara-fechara-7-lojas-no-brasil-incluindo-unidade-de-goiania.jpg'
        },
      ],
      search: "",
      select: null,
      options: [
        {
          value: null, text: 'Selecione um Status'
        },
        {
          value: 1, text: 'Ativo'
        },
        {
          value: 0, text: 'Inativo'
        }
      ]
    }
  },
  methods: {
    initExcel(x){
      const data = [this.data[x]];

      const fileName = `${data[0].nome}_relatorio.xls`;

      const ws = XLSX.utils.json_to_sheet(data);
      console.log(data)
      const wb = XLSX.utils.book_new();
      XLSX.utils.book_append_sheet(wb, ws, 'export');
      XLSX.writeFile(wb, fileName);
    },

    saveAsExcel(){
      const data = this.data;

      const fileName = `relatorio_geral.xls`;

      const ws = XLSX.utils.json_to_sheet(data);
      console.log(data)
      const wb = XLSX.utils.book_new();
      XLSX.utils.book_append_sheet(wb, ws, 'export');
      XLSX.writeFile(wb, fileName);
    },

    limparFiltro(){
      this.search = "";
      this.select = null;
    }
  },
  computed:{
    itemsFiltered(){
      let valores = [];
      valores = this.data.filter((item) => {
        return (
          item.nome.toLowerCase().indexOf(this.search.toLowerCase()) > -1 || item.email.toLowerCase().indexOf(this.search.toLowerCase()) > -1
        );
      });

      valores = valores.filter((item) => {
        if(this.select === null){
          return item;
        }

        return item.statusEmpresa === this.select;
      });

      return valores;
    }
  }
}
</script>

<style scoped>
</style>