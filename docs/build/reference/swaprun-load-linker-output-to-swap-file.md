---
title: "/SWAPRUN (Cargar resultados del vinculador en el archivo de intercambio) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.SwapRunFromNet"
  - "/swaprun"
  - "VC.Project.VCLinkerTool.SwapRunFromCD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SWAPRUN (opción del vinculador)"
  - "archivos [C++], LINK"
  - "LINK (herramienta) [C++], resultado"
  - "vinculador [C++], copiar los resultados a un archivo de intercambio"
  - "archivos de salida, vinculador"
  - "archivo de intercambio para los resultados del vinculador"
  - "SWAPRUN (opción del vinculador)"
  - "-SWAPRUN (opción del vinculador)"
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SWAPRUN (Cargar resultados del vinculador en el archivo de intercambio)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SWAPRUN:{NET|CD}  
```  
  
## Comentarios  
 La opción \/SWAPRUN indica al sistema operativo que copie el resultado del vinculador en un archivo de intercambio en primer lugar y, a continuación, ejecute la imagen desde este.  Esta es una característica de Windows NT 4.0 \(y posterior\).  
  
 Si se especifica la opción de NET, el sistema operativo copiará primero la imagen binaria de la red en un archivo de intercambio y la cargará desde este.  Esta opción resulta útil para ejecutar aplicaciones a través de la red.  Si se especifica CD, el sistema operativo copiará la imagen de un disco extraíble en un archivo de paginación y después la cargará.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Sistema**.  
  
4.  Modifique una de las propiedades siguientes:  
  
    -   **Ejecutar intercambio desde CD**  
  
    -   **Ejecutar intercambio desde red**  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)