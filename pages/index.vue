<template>
  <div>
    <div class="container d-flex flex-wrap justify-content-between">
      <div class="row" v-for="empresa in data" :key="empresa">
        <CardEmpresa :nome="empresa.nome" :codigo="empresa.codigo" :cnpj="empresa.cnpj" :razaoSocial="empresa.razaoSocial" :inscricaoMunicipal="empresa.inscricaoMunicipal" :dataInclusao="empresa.dataInclusao" :statusEmpresa="empresa.statusEmpresa" :responsavelLegal="empresa.responsavelLegal" :email="empresa.email" :telefoneContato="empresa.telefoneContato" :img="empresa.img"  />
      </div>
    </div>
  </div>
</template>

<script>
export default {

  data(){
    return{
      data: [
        {
          nome: 'Super Show Bis',
          codigo: '1541851',
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
          codigo: '2216541',
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
          codigo: '359865',
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
          codigo: '41541',
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
          codigo: '52652',
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
          nome: 'Riachuelo',
          codigo: '65166',
          cnpj: '8.895.234/2343-54',
          razaoSocial: 'Vestuário',
          inscricaoMunicipal: '532432',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Flávio Rocha',
          email: 'rchlo@riachuelo.com',
          telefoneContato: '(84) 3423-5421',
          img: 'https://veja.abril.com.br/wp-content/uploads/2020/06/Riachuelo-Fachada.jpg?quality=70&strip=info&w=656'
        },
        {
          nome: 'Adm. Arena das Dunas',
          codigo: '67655',
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
          codigo: '681221',
          cnpj: '8.895.241/5154-54',
          razaoSocial: 'Construtora',
          inscricaoMunicipal: '126314',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Higor Dubeux',
          email: 'mdbr@dubeux.com',
          telefoneContato: '(84) 4234-5421',
          img: 'https://yt3.ggpht.com/ytc/AKedOLRlVoneqJB14f1ChCcyClPqP2ScYRqj7uDaMX_BAQ=s900-c-k-c0x00ffffff-no-rj'
        },
        {
          nome: 'Riachuelo',
          codigo: '691215',
          cnpj: '8.895.234/2343-54',
          razaoSocial: 'Vestuário',
          inscricaoMunicipal: '532432',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Flávio Rocha',
          email: 'rchlo@riachuelo.com',
          telefoneContato: '(84) 3423-5421',
          img: 'https://veja.abril.com.br/wp-content/uploads/2020/06/Riachuelo-Fachada.jpg?quality=70&strip=info&w=656'
        },
        {
          nome: 'Viação nordeste',
          codigo: '675262',
          cnpj: '8.823.434/4341-54',
          razaoSocial: 'Transporte',
          inscricaoMunicipal: '565984',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Flávio Rocha',
          email: 'viacao@nordeste.com',
          telefoneContato: '(84) 5456-1251',
          img: 'https://s2.glbimg.com/GZhacxriIbuGHPUAZJTzI7Slj9M=/0x258:1632x1224/984x0/smart/filters:strip_icc()/i.s3.glbimg.com/v1/AUTH_59edd422c0c84a879bd37670ae4f538a/internal_photos/bs/2020/8/J/JwgdnORnCoQDkZvy5q1A/viacao-nordeste.jpeg'
        },
        {
          nome: 'Natal Computer',
          codigo: '6815151',
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
          codigo: '6911515',
          cnpj: '8.895.999/2343-54',
          razaoSocial: 'Vestuário',
          inscricaoMunicipal: '123454',
          dataInclusao: '',
          statusEmpresa: 0,
          responsavelLegal: 'Paul McCartney',
          email: 'zara@zara.com',
          telefoneContato: '(84) 3242-1231',
          img: 'https://files.aredacao.com.br/upload/content/zara-fechara-7-lojas-no-brasil-incluindo-unidade-de-goiania.jpg'
        },
      ]
    }
  }

}
</script>
