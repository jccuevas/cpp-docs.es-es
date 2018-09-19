---
title: -WHOLEARCHIVE (incluir todos los archivos de objeto de biblioteca) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3a59ed53227e0c9bf598f96b1bb72247a3341b0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722259"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (incluir todos los archivos de objeto de biblioteca)

Fuerza al vinculador que incluya todos los archivos de objeto en la biblioteca estática en el archivo ejecutable vinculado.

## <a name="syntax"></a>Sintaxis

> /WHOLEARCHIVE [:*biblioteca*]

## <a name="remarks"></a>Comentarios

La opción /WHOLEARCHIVE fuerza al vinculador que incluya todos los archivos objeto desde una biblioteca estática especificada, o si no se especifica ninguna biblioteca, de todas las bibliotecas estáticas especificadas para el vínculo de comando. Para especificar la opción /WHOLEARCHIVE para varias bibliotecas, puede usar más de un conmutador /WHOLEARCHIVE en la línea de comandos del vinculador. De forma predeterminada, el vinculador incluye archivos de objeto en la salida vinculada solo si se exportan los símbolos que se hace referencia a otros archivos de objeto en el archivo ejecutable. La opción /WHOLEARCHIVE hace que el enlazador trate todos los archivos de objeto que se archiva en una biblioteca estática como si se especificaron individualmente en la línea de comandos del vinculador.

La opción /WHOLEARCHIVE puede utilizarse para volver a exportar todos los símbolos de una biblioteca estática. Esto le permite asegurarse de que todo el código de biblioteca, recursos y los metadatos se incluyen al crear un componente de más de una biblioteca estática. Si ve la advertencia LNK4264 al crear una biblioteca estática que contiene los componentes de Windows en tiempo de ejecución para la exportación, utilice la opción /WHOLEARCHIVE al vincular esa biblioteca en otra aplicación o componente.

La opción /WHOLEARCHIVE se introdujo en Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **línea de comandos** página de propiedades bajo **propiedades de configuración**, **vinculador**.

1. Agregue la opción de /WHOLEARCHIVE el **opciones adicionales** cuadro de texto.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)