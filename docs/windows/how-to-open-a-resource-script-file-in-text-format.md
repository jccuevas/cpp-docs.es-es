---
title: "Cómo: abrir un archivo de Script de recursos en formato de texto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resource
dev_langs: C++
helpviewer_keywords:
- resource script files, opening in text format
- .rc files, opening in text format
- rc files, opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 19f6a105b255fd5ab4ecb777cc52cccf7a978b7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Cómo: Abrir un archivo de script de recursos en formato de texto
Puede haber ocasiones en que desee ver el contenido del archivo de script de recursos (.rc) del proyecto sin abrir un recurso, como un cuadro de diálogo, en su editor de recursos específico. Por ejemplo, es posible que desee buscar una cadena en todos los cuadros de diálogo del archivo de recursos sin tener que abrir cada uno de ellos independientemente.  
  
> [!NOTE]
>  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
 Puede abrir fácilmente el archivo de recursos en formato de texto para ver todos los recursos contiene y realizar operaciones globales admitidas por la [editor de texto](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).  
  
> [!NOTE]
>  Los editores de recursos no leen directamente los archivos .rc o resource.h. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como en un proceso de compilación normal, la información que no es simbólica (por ejemplo, los comentarios) se descarta durante el proceso de compilación. Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar (por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc. Para obtener información acerca de cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).  
  
### <a name="to-open-a-resource-script-file-as-text"></a>Para abrir un archivo de script de recursos como texto  
  
1.  Desde el **archivo** menú, elija **abiertos**, a continuación, haga clic en **archivo.**  
  
2.  En el **archivos abiertos** cuadro de diálogo, navegue hasta el archivo de script de recursos que desea ver en formato de texto.  
  
3.  Resalte el archivo, a continuación, haga clic en la flecha de lista desplegable en el **abiertos** (situado a la derecha del botón).  
  
4.  Elija **abrir con** en el menú desplegable.  
  
5.  En el **abrir con** cuadro de diálogo, haga clic en **Editor de código fuente (texto)**.  
  
6.  Desde el **abrir como** lista desplegable, seleccione **texto**.  
  
     El recurso se abre en el editor de código fuente.  
  
 \- o -  
  
1.  En **el Explorador de soluciones**, haga clic en el archivo .rc.  
  
2.  En el menú contextual, elija **abrir con...** , a continuación, seleccione **Editor de código fuente (texto)**.  
  

  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)