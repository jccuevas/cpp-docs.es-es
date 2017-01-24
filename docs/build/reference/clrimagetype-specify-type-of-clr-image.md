---
title: "/CLRIMAGETYPE (Especificar tipo de imagen CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRIMAGETYPE"
  - "VC.Project.VCLinkerTool.CLRImageType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRIMAGETYPE (opción del vinculador)"
  - "-CLRIMAGETYPE (opción del vinculador)"
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRIMAGETYPE (Especificar tipo de imagen CLR)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## Comentarios  
 El vinculador acepta los objetos nativos y también los objetos de MSIL que se compilan con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md), \/clr:pure o \/clr:safe.  Cuando se pasan objetos mixtos en la misma compilación, la capacidad de comprobar el archivo de salida será, de forma predeterminada, igual al nivel inferior de la capacidad de comprobar los módulos de entrada.  Por ejemplo, si pasa un módulo seguro y uno puro al vinculador, el archivo de salida será puro.  Si pasa una imagen nativa y una imagen de modo mixto \(compilada mediante **\/clr**\), la imagen resultante será una imagen de modo mixto.  
  
 Puede usar \/CLRIMAGETYPE para especificar un nivel inferior de capacidad de comprobación si es lo que necesita.  
  
 En .NET 4.5, \/CLRIMAGETYPE admite una opción de SAFE32BITPREFERRED.  Esto establece \(en el encabezado del archivo PE de la imagen\) las marcas que indican que los objetos de MSIL son seguros y se pueden ejecutar en todas las plataformas, pero que se prefieren los entornos de ejecución de 32 bits.  Esta opción permite que una aplicación se ejecute en plataformas ARM y también especifica que se debe ejecutar bajo WOW64 en los sistemas operativos de 64 bits, en lugar de utilizar el entorno de ejecución de 64 bits.  
  
 Cuando se ejecuta un archivo .exe que se ha compilado con **\/clr** o **\/clr:pure** en un sistema operativo de 64 bits, la aplicación se ejecuta bajo WOW64, que permite la ejecución de una aplicación de 32 bits en un sistema operativo de 64 bits.  De forma predeterminada, un archivo .exe compilado con **\/clr:safe** se ejecuta bajo compatibilidad de 64 bits del sistema operativo.  Sin embargo, es posible que la aplicación segura cargue un componente de 32 bits.  En ese caso, una imagen segura que se ejecute bajo la compatibilidad de 64 bits del sistema operativo no podrá cargar la aplicación de 32 bits y se producirá un error.  Para asegurarse de que una imagen segura continuará ejecutándose cuando cargue un componente de 32 bits en un sistema operativo de 64 bits, utilice la opción \/CLRIMAGETYPE:SAFE32BITPREFERRED.  Si el código no tiene que ejecutarse en plataformas ARM, puede especificar la opción \/CLRIMAGETYPE:PURE para cambiar los metadatos \(.corflags\) y marcarla para que se ejecute bajo WOW64 \(y sustituya su propio token de entrada\):  
  
 **cl \/clr:safe t.cpp \/link \/clrimagetype:pure \/entry:?main@@$$HYMHXZ \/subsystem:console**  
  
 Para obtener información acerca de cómo determinar el tipo de imagen de CLR de un archivo, vea [\/CLRHEADER](../../build/reference/clrheader.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Tipo de imagen de CLR**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)