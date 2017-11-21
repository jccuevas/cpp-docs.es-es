---
title: "Cómo: copiar recursos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e3ec6fad52a5f999ada9e4ce6df608098c28399c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-copy-resources"></a>Cómo: Copiar recursos
Puede copiar recursos de un archivo a otro sin modificarlas o puede [cambiar el idioma o la condición de un recurso al copiarlo](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).  
  
 Puede copiar fácilmente recursos de un recurso existente o un archivo ejecutable en el archivo de recursos actual. Para ello, abre los archivos que contienen recursos al mismo tiempo y arrastra elementos desde un archivo a otro o copia y pega entre los dos archivos. Este método funciona para los archivos de recursos (.rc) de la secuencia de comandos y archivos de recursos (.rct) de la plantilla, así como archivos ejecutables (.exe).  
  
> [!NOTE]
>  Visual C++ incluye archivos de recursos de ejemplo que puede usar en su propia aplicación. Para obtener más información, consulte [CLIPART: recursos comunes](http://msdn.microsoft.com/en-us/9bac2891-b6b3-49ec-a287-cec850c707e0).  
  
 Puede usar el método de arrastrar y colocar entre archivos .rc que estén abiertos [fuera del proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Para copiar recursos entre archivos mediante el método de arrastrar y colocar  
  
1.  Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo fuera de un proyecto de .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, abra Source1.rf y Source2.rc.  
  
2.  En el primer archivo .rc, haga clic en el recurso que se va a copiar. Por ejemplo, en Source1.RF, haga clic en IDD_DIALOG1.  
  
3.  Mantenga presionada la tecla CTRL y arrastre el recurso para el segundo archivo. rc. Por ejemplo, arrastre IDD_DIALOG1 desde Source1.RF a Source2.rc.  
  
    > [!NOTE]
    >  Si arrastra el recurso sin mantener presionada la tecla CTRL, mueve el recurso, en lugar de copiarlo.  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>Para copiar recursos con copiar y pegar  
  
1.  Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo fuera de un proyecto de .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, Source1.RF y Source2.rc.  
  
2.  En el archivo de origen desde el que desea copiar un recurso (por ejemplo, Source1.RF), haga clic en un recurso y elija **copia** en el menú contextual.  
  
3.  Haga clic en el archivo de recursos en la que desea pegar el recurso (por ejemplo, Source2.rc). Elija **pegar** en el menú contextual.  
  
    > [!NOTE]
    >  No se puede arrastrar y colocar, copiar, cortar o pegar entre archivos de recursos en el proyecto (vista de recursos) y archivos .rc independientes (aquellas abiertos en ventanas de documento). Puede hacerlo en las versiones anteriores del producto.  
  
    > [!NOTE]
    >  Para evitar conflictos con nombres de símbolos o valores en el archivo existente, Visual C++ puede cambiar valor de símbolo del recurso transferido o nombre de símbolo y el valor cuando se copia en el nuevo archivo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](https://msdn.microsoft.com/library/f45fce5x.aspx) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](https://msdn.microsoft.com/library/xbx3z216.aspx). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Cómo: abrir un archivo de Script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)