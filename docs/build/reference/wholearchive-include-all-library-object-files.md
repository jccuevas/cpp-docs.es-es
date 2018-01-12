---
title: -WHOLEARCHIVE (incluir todos los archivos de objeto de biblioteca) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3499d6583c7d9801aa4c3b12c66196c975b192ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (incluir todos los archivos de objeto de biblioteca)
Fuerza al vinculador que incluya todos los archivos de objeto en la biblioteca estática en el archivo ejecutable vinculado.  
  
## <a name="syntax"></a>Sintaxis  
  
> / WHOLEARCHIVE [:*biblioteca*]  
  
## <a name="remarks"></a>Comentarios  
  
La opción /WHOLEARCHIVE fuerza al vinculador que debe incluir todos los archivos objeto desde una biblioteca estática especificada o si se ha especificado ninguna biblioteca, de todas las bibliotecas estáticas especificadas para el vínculo de comando. Para especificar la opción /WHOLEARCHIVE para varias bibliotecas, puede usar más de un conmutador de /WHOLEARCHIVE en la línea de comandos del vinculador. De forma predeterminada, el vinculador incluye archivos de objeto en la salida vinculada solo si exportan símbolos hace referencia a otros archivos de objeto en el archivo ejecutable. La opción /WHOLEARCHIVE hace que el vinculador trate todos los archivos objeto archivados en una biblioteca estática como si se especificaron individualmente en la línea de comandos del vinculador.  
  
La opción /WHOLEARCHIVE puede utilizarse para volver a exportar todos los símbolos de una biblioteca estática. Esto le permite asegurarse de que todo el código de biblioteca, los recursos y los metadatos se incluyen al crear un componente de más de una biblioteca estática. Si ve la advertencia LNK4264 cuando se crea una biblioteca estática que contiene los componentes en tiempo de ejecución de Windows para la exportación, utilice la opción de /WHOLEARCHIVE al vincular dicha biblioteca en otra aplicación o componente.  
  
La opción /WHOLEARCHIVE se introdujo en Visual Studio 2015 Update 2.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
1.  Seleccione el **línea de comandos** página de propiedades bajo **propiedades de configuración**, **vinculador**.  
  
1.  Agregar la opción de /WHOLEARCHIVE el **opciones adicionales** cuadro de texto.  
  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)