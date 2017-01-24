---
title: "Error de las herramientas del vinculador LNK1123 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1123"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1123"
ms.assetid: fe47af69-0f42-4792-9133-541192cd8514
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1123
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error durante la conversión a COFF: archivo no válido o dañado  
  
 Los archivos de entrada deben tener el formato de archivo de objeto común \(COFF\).  Si un archivo de entrada no tiene el formato COFF, el vinculador intenta convertir automáticamente los objetos OMF de 32 bits a COFF o ejecuta CVTRES.EXE para convertir los archivos de recursos.  Este mensaje indica que el vinculador no pudo convertir el archivo.  También puede ocurrir al usar una versión incompatible de CVTRES.EXE desde otra instalación de Visual Studio, el kit de desarrollo de Windows o .NET Framework.  
  
> [!NOTE]
>  Si está ejecutando una versión anterior de Visual Studio, la conversión automática puede no ser compatible.  
  
### Para corregir el problema  
  
-   Aplique todos los service packs y actualizaciones para su versión de Visual Studio.  Esto es especialmente importante para Visual Studio 2010.  
  
-   Intente compilar con la vinculación incremental deshabilitada.  En la barra de menús, seleccione **Proyecto**, **Propiedades**.  En el cuadro de diálogo **Páginas de propiedades**, expanda **Propiedades de configuración**, **Vinculador**.  Cambie el valor de **Habilitar vinculación incremental** a **No**.  
  
-   Compruebe que la versión de CVTRES.EXE que se encuentra primero en la variable de entorno PATH coincide con la versión de las herramientas de compilación, o la versión del conjunto de herramientas de la plataforma, utilizada por el proyecto.  
  
-   Pruebe a desactivar la opción Incrustar manifiesto.  En la barra de menús, seleccione **Proyecto**, **Propiedades**.  En el cuadro de diálogo **Páginas de propiedades**, expanda **Propiedades de configuración**, **Herramienta Manifiesto**, **Entrada y salida**.  Cambie el valor de **Incrustar manifiesto** a **No**.  
  
-   Asegúrese de que el tipo de archivo es válido.  Por ejemplo, asegúrese de que un objeto OMF es de 32 bits y no de 16 bits.  Para más información, vea [Archivos .obj como entrada del vinculador](../../build/reference/dot-obj-files-as-linker-input.md) y [Especificación de Microsoft PE y COFF](http://go.microsoft.com/fwlink/p/?LinkId=93292).  
  
-   Compruebe que el archivo no está dañado.  Vuelva a compilar, si es necesario.  
  
## Vea también  
 [Archivos .obj como entrada del vinculador](../../build/reference/dot-obj-files-as-linker-input.md)   
 [Referencia de EDITBIN](../../build/reference/editbin-reference.md)   
 [Referencia de DUMPBIN](../../build/reference/dumpbin-reference.md)