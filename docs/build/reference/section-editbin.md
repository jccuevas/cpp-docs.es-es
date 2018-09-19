---
title: -SECTION (EDITBIN) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f91d467681d5a4d5bf4eaa5f042ef44b87810b3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701994"
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

[Opciones de EDITBIN](../../build/reference/editbin-options.md)