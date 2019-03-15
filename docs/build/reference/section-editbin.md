---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 8bcc925b34118630c872a0147b93291626b7c19b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822436"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Comentarios

Esta opción cambia los atributos de una sección reemplazando los atributos que se establecieron cuando se compiló o vinculó el archivo de objeto de la sección.

Después de los dos puntos ( **:** ), especifique el *nombre* de la sección. Para cambiar el nombre de sección, siga *nombre* con un signo igual (=) y un *newname* para la sección.

Para establecer o cambiar la sección `attributes`, especificar una coma (**,**) seguido de uno o más caracteres de los atributos. Para invalidar un atributo, preceden su carácter con un signo de exclamación (!). Los caracteres siguientes especifican atributos de memoria:

|Atributo|Parámetro|
|---------------|-------------|
|c|code|
|d|Puede descartar|
|h|ejecutable|
|i|datos inicializados|
|k|memoria virtual almacenado en caché|
|m|Quitar vínculo|
|o|información de vínculo|
|p|memoria virtual paginada|
|r|leer|
|s|shared|
|u|datos sin inicializar|
|s|escribir|

Para controlar *alineación*, especifique el carácter **A** seguido de uno de los caracteres siguientes para establecer el tamaño de alineación en bytes, como se indica a continuación:

|Carácter|Tamaño de alineación en bytes|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|m|32|
|s|64|
|x|sin alineación|

Especifique el `attributes` y *alineación* caracteres como una cadena con ningún espacio en blanco. Los caracteres no distinguen mayúsculas de minúsculas.

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)
