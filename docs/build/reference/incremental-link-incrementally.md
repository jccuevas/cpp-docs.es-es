---
title: "/INCREMENTAL (Vincular de forma incremental) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/incremental"
  - "VC.Project.VCLinkerTool.LinkIncremental"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INCREMENTAL (opción del vinculador)"
  - "INCREMENTAL (opción del vinculador)"
  - "-INCREMENTAL (opción del vinculador)"
  - "vinculación incremental"
  - "vincular de forma incremental (opción)"
  - "LINK (herramienta) [C++], opciones para vínculos completos"
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /INCREMENTAL (Vincular de forma incremental)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/INCREMENTAL[:NO]  
```  
  
## Comentarios  
 Controla el modo en que el vinculador administra la vinculación incremental.  
  
 De manera predeterminada, el vinculador se ejecuta en modo incremental.  Para reemplazar un vínculo incremental predeterminado, especifique \/INCREMENTAL:NO.  
  
 Un programa vinculado de forma incremental tiene una funcionalidad equivalente a un programa vinculado de forma no incremental.  Sin embargo, al estar preparados para posteriores vínculos incrementales, los archivos ejecutables \(.exe\) vinculados incrementalmente y las bibliotecas de vínculos dinámicos \(DLL\):  
  
-   A causa del relleno del código y los datos, un tendrán tamaño mayor que los programas vinculados de manera no incremental. \(El relleno permite al vinculador aumentar el tamaño de las funciones y los datos sin tener que volver a crear el archivo .exe\).  
  
-   Pueden contener códigos thunk de salto para controlar la reubicación de las funciones en direcciones nuevas.  
  
    > [!NOTE]
    >  Para asegurarse de que la versión final de lanzamiento no contiene relleno ni códigos thunk, vincule el programa de forma no incremental.  
  
 Para vincular de forma incremental con independencia del valor predeterminado, especifique \/INCREMENTAL.  Si, al seleccionar esta opción, el vinculador no puede establecer el vínculo de forma incremental, emitirá una advertencia y, después, vinculará el programa de manera no incremental.  Hay ciertas opciones y situaciones que invalidan la opción \/INCREMENTAL.  
  
 La mayoría de los programas pueden vincularse de manera incremental.  Sin embargo, algunos cambios son demasiado grandes y algunas opciones no son compatibles con la vinculación incremental.  LINK realizará un vínculo completo si se especifica cualquiera de las opciones siguientes:  
  
-   No se selecciona la vinculación incremental \(\/INCREMENTAL:NO\).  
  
-   Se selecciona \/OPT:REF.  
  
-   Se selecciona \/OPT:ICF.  
  
-   Se selecciona \/OPT:LBR.  
  
-   Se selecciona \/ORDER.  
  
 La opción \/INCREMENTAL está implícita cuando se especifica [\/DEBUG](../../build/reference/debug-generate-debug-info.md).  
  
 Asimismo, LINK realizará un vínculo completo si se da alguna de las situaciones siguientes:  
  
-   Falta el archivo de estado incremental \(.ilk\). \(LINK crea un archivo .ilk nuevo en previsión de una vinculación incremental posterior\).  
  
-   No se cuenta con permiso de escritura para el archivo .ilk. \(LINK omite el archivo .ilk y produce un vínculo no incremental\).  
  
-   Falta el archivo de salida .exe o .dll.  
  
-   Se ha modificado la marca de tiempo del archivo .ilk, .exe o .dll.  
  
-   Se ha modificado una opción de LINK.  La mayoría de las opciones de LINK, si se cambian entre compilaciones, producen un vínculo completo.  
  
-   Se ha agregado u omitido un archivo objeto \(.obj\).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione la carpeta **Vinculador**.  
  
3.  Seleccione la página de propiedades **General**.  
  
4.  Modifique la propiedad **Habilitar vinculación incremental**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)