---
title: "/ALLOWISOLATION (Manifestar bucle) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ALLOWISOLATION"
  - "VC.Project.VCLinkerTool.AllowIsolation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWISOLATION (opción del vinculador)"
  - "-ALLOWISOLATION (opción del vinculador)"
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /ALLOWISOLATION (Manifestar bucle)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el comportamiento para búsqueda de manifiestos.  
  
## Sintaxis  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## Comentarios  
 **\/ALLOWISOLATION:NO** indica que los archivos DLL se cargan como si no hubiese manifiesto y provoca que el vinculador establezca el bit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` en el campo opcional `DllCharacteristics` del encabezado.  
  
 **\/ALLOWISOLATION** provoca que el sistema operativo realice búsquedas y cargas de manifiestos.  
  
 **\/ALLOWISOLATION** es el valor predeterminado.  
  
 Si se ha deshabilitado el aislamiento para una aplicación ejecutable, el cargador de Windows no intentará buscar un manifiesto de la aplicación para el proceso recién creado.  El nuevo proceso no tendrá un contexto de activación, incluso si hay un manifiesto dentro del ejecutable o situado en el mismo directorio que el ejecutable con el nombre *executable\-name***.exe.manifest**.  
  
 Para obtener más información, vea [Referencia de archivos de manifiesto](http://msdn.microsoft.com/library/aa375632).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Archivo de manifiesto**.  
  
5.  Modifique la propiedad **Permitir aislamiento**.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)