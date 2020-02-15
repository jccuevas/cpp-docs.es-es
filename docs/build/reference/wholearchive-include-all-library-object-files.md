---
title: /WHOLEARCHIVE (incluir todos los archivos de objeto de biblioteca)
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 95685c9c0dfde45c42449bbcad67228a0e21b36a
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257538"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (incluir todos los archivos de objeto de biblioteca)

Obligue al enlazador a incluir todos los archivos objeto de la biblioteca estática en el ejecutable vinculado.

## <a name="syntax"></a>Sintaxis

> \ **/WHOLEARCHIVE**
> **/WHOLEARCHIVE:** _biblioteca_

### <a name="arguments"></a>Argumentos

*biblioteca*\
Un nombreruta opcional para una biblioteca estática. El vinculador incluye todos los archivos objeto de esta biblioteca.

## <a name="remarks"></a>Observaciones

La opción/WHOLEARCHIVE obliga al vinculador a incluir todos los archivos objeto de una biblioteca estática especificada, o bien, si no se ha especificado ninguna biblioteca, de todas las bibliotecas estáticas especificadas para el comando LINK. Para especificar la opción/WHOLEARCHIVE para varias bibliotecas, puede usar más de un conmutador/WHOLEARCHIVE en la línea de comandos del vinculador. De forma predeterminada, el vinculador solo incluye archivos objeto en la salida vinculada Si exporta los símbolos a los que hacen referencia otros archivos objeto del archivo ejecutable. La opción/WHOLEARCHIVE hace que el vinculador trate todos los archivos objeto archivados en una biblioteca estática como si se hubieran especificado individualmente en la línea de comandos del vinculador.

La opción/WHOLEARCHIVE se puede usar para volver a exportar todos los símbolos de una biblioteca estática. Esto le permite asegurarse de que todo el código de biblioteca, los recursos y los metadatos se incluyen al crear un componente a partir de más de una biblioteca estática. Si ve la advertencia LNK4264 al crear una biblioteca estática que contiene Windows Runtime componentes para la exportación, use la opción/WHOLEARCHIVE al vincular esa biblioteca a otro componente o aplicación.

La opción/WHOLEARCHIVE se presentó en Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **línea de comandos** en **propiedades de configuración**, **enlazador**.

1. Agregue la opción/WHOLEARCHIVE al cuadro de texto **opciones adicionales** .

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
