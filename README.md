SIGEPWeb - Correios
===================

[![Travis branch](https://img.shields.io/travis/mstuttgart/pysigep/develop.svg?style=flat-square)](https://travis-ci.org/mstuttgart/pysigep)
[![Coveralls branch](https://img.shields.io/coveralls/mstuttgart/pysigep/develop.svg?style=flat-square)](https://coveralls.io/github/mstuttgart/pysigep?branch=develop)
[![Code Health](https://landscape.io/github/mstuttgart/pysigep/develop/landscape.svg?style=flat-square)](https://landscape.io/github/mstuttgart/pysigep/develop)
[![PyPI](https://img.shields.io/pypi/status/pysigep.svg?style=flat-square)]()
[![PyPI](https://img.shields.io/pypi/v/pysigep.svg?style=flat-square)](https://pypi.python.org/pypi/pysigep)
[![PyPI](https://img.shields.io/pypi/pyversions/pysigep.svg?style=flat-square)]()
[![PyPI](https://img.shields.io/pypi/l/pysigep.svg?style=flat-square)](https://github.com/mstuttgart/pysigep/blob/develop/LICENSE)

Implementação do sistema SIGEP Web em Python permitindo integração com Web Service do Correios. O Módulo funciona como uma interface de consulta para os métodos fornecidos pelo webservice.

## Recursos

- [x] Verificar *status* de um Cartão de Postagem
- [x] Obter dados do endereço a partir de seu respectivo CEP.
- [x] Verificar disponibilidade de um dado serviço.  
- [x] Gerar etiquetas para postagem de mercadoria.
- [x] Criação da pré-lista de postagem (PLP) e envio de seu XML para o webservice dos Correios.
- [ ] Imprimir etiqueta da PLP.
- [x] Imprimir Chancela.
- [ ] Rotinas de logística reversa.
- [ ] Calcula frete e prazo de entrega.

## Instalação

A versão atual **ainda esta em fase de desenvolvimento**, sendo que os recursos disponiveis podem ser removidos sem aviso prévio. Portanto, não é recomendável seu uso em ambiente de produção.

## Dependências

As dependências do projeto estão listadas no arquivo `requeriments.txt`.

```bash
pip install -r requeriments.txt
```

## Como usar

```python
# -*- coding: utf-8 -*-
from pysigep.sigep import cep_consulta
from pysigep.sigep import verifica_disponibilidade_servico

# Executando a consulta de CEP

cep = {'cep': '83010140'}
consulta = cep_consulta(**cep)

print consulta.bairro
print consulta.cep
print consulta.cidade
print consulta.complemento
print consulta.complemento2
print consulta.end
print consulta.id
print consulta.uf

# Verificando disponibilidade de serviço

usuario = {
    'codAdministrativo': '08082650',
    'numeroServico': '40215',
    'cepOrigem': '70002900',
    'cepDestino': '81350120',
    'usuario': 'sigep',
    'senha': 'n5f9t8',
}

with self.assertRaises(Exception):
    print verifica_disponibilidade_servico(**usuario)


# Solicitando etiquetas

solicitacao = {
    'usuario': 'sigep',
    'senha': 'n5f9t8',
    'identificador': '34028316000103',
    'idServico': '104625',
    'qtdEtiquetas': '10',
}
with self.assertRaises(Exception):
    print solicita_etiquetas_com_dv(**solicitacao)

```

#### Executando os testes
Caso você deseje executar os testes, basta usar o comando abaixo (necessário estar conectado à internet):

```bash
python setup.py test
```

## Contribuindo
Encontrou algum erro? Quer adicionar alguma *feature* nova ao projeto? Faça um *fork* deste repositório e me envie um *Pull Request*. Contribuições sempre são bem vindas.

### Contribuidores
* [Alessandro Martini](https://github.com/martini97)
* [Danimar Ribeiro](https://github.com/danimaribeiro)
* [Michel Sabchuk](https://github.com/michelts)

## SigepWeb Docs
* [Manual SigepWeb](http://www.corporativo.correios.com.br/encomendas/sigepweb/doc/Manual_de_Implementacao_do_Web_Service_SIGEPWEB_Logistica_Reversa.pdf)
