---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438916"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Observaciones

Esta opción cambia los atributos de una sección, invalidando los atributos que se establecieron al compilar o vincular el archivo objeto de la sección.

Después del signo de dos puntos ( **:** ), especifique el *nombre* de la sección. Para cambiar el nombre de la sección, siga el *nombre* con un signo igual (=) y un *NewName* en la sección.

Para establecer o cambiar el `attributes`de la sección, especifique una coma ( **,** ) seguida de uno o varios caracteres de atributo. Para negar un atributo, anteponga un signo de exclamación (!) a su carácter. Los siguientes caracteres especifican atributos de memoria:

|Atributo|Configuración|
|---------------|-------------|
|c|código|
|d|descartable|
|e|ejecutable|
|i|datos inicializados|
|k|memoria virtual almacenada en caché|
|m|quitar vínculo|
|o|información de vínculo|
|p|memoria virtual paginada|
|r|leer|
|s|compartido|
|u|datos no inicializados|
|w|escritura|

Para controlar la *alineación*, especifique el carácter **a** seguido de uno de los siguientes caracteres para establecer el tamaño de la alineación en bytes, como se indica a continuación:

|Carácter|Tamaño de alineación en bytes|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|sin alineación|

Especifique los caracteres de *alineación* y `attributes` como una cadena sin espacios en blanco. Los caracteres no distinguen mayúsculas de minúsculas.

## <a name="see-also"></a>Consulte también

[Opciones de EDITBIN](editbin-options.md)
