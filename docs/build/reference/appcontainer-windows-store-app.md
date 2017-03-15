---
title: "/APPCONTAINER (aplicaci&#243;n de la Tienda Windows) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /APPCONTAINER (aplicaci&#243;n de la Tienda Windows)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica si el vinculador crea una imagen ejecutable que se debe ejecutar en un contenedor de la aplicación.  
  
## Sintaxis  
  
```  
/APPCONTAINER[:NO]  
```  
  
## Comentarios  
 De forma predeterminada, \/APPCONTAINER está desactivado.  
  
 Esta opción modifica un ejecutable para indicar si la aplicación se debe ejecutar en el entorno del proceso de aislamiento del proceso de appcontainer.  Especifique \/APPCONTAINER para una aplicación que deberá ejecutarse en el entorno de appcontainer, por ejemplo, una aplicación [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)]. \(La opción se establece automáticamente en Visual Studio al crear una aplicación [!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)] desde una plantilla.\) Para una aplicación de escritorio, especifique \/APPCONTAINER:NO o simplemente omita la opción.  
  
 La opción \/APPCONTAINER se introdujo en [!INCLUDE[win8](../../build/includes/win8_md.md)].  
  
### Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Línea de comandos**.  
  
5.  En **Opciones adicionales**, escriba `/APPCONTAINER` o `/APPCONTAINER:NO`.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)