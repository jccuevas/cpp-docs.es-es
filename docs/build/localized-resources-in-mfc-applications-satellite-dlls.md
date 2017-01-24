---
title: "Recursos localizados en aplicaciones MFC: archivos DLL sat&#233;lite | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], localizar en MFC"
  - "localización [C++], MFC (recursos)"
  - "recursos localizados [C++]"
  - "DLL de MFC [C++], adaptar"
  - "compatibilidad con varios lenguajes [C++]"
  - "DLL sólo de recursos [C++]"
  - "DLL sólo de recursos [C++], MFC (aplicaciones)"
  - "recursos [MFC], adaptar"
  - "DLL satélite [C++]"
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Recursos localizados en aplicaciones MFC: archivos DLL sat&#233;lite
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La versión 7.0 de MFC y posterior proporciona compatibilidad mejorada con archivos DLL satélite, una característica que le ayuda a crear aplicaciones en múltiples idiomas.  Un archivo DLL satélite es un [archivo DLL de sólo recursos](../build/creating-a-resource-only-dll.md) que contiene los recursos de una aplicación localizados en un lenguaje en particular.  Cuando la aplicación empieza a ejecutarse, MFC carga automáticamente el recurso localizado más adecuado para el entorno.  Por ejemplo, podría tener una aplicación con recursos en inglés y dos archivos DLL satélite, uno que contenga la traducción al francés de los recursos y, otro, la traducción al alemán.  Cuando la aplicación se ejecuta en un sistema en idioma inglés, utiliza los recursos en inglés.  Si se ejecuta en un sistema en idioma francés, utiliza los recursos en francés; y lo mismo para un sistema en alemán.  
  
 Para admitir recursos localizados en una aplicación MFC, MFC intenta cargar un archivo DLL satélite que contenga los recursos localizados en ese idioma específico.  Los archivos DLL satélite se denominan *NombreAplicaciónXXX*.dll, donde *NombreAplicación* es el nombre del archivo .exe o .dll que utiliza MFC y *XXX* el código de tres letras para el idioma de los recursos \(por ejemplo, 'ENU' o 'DEU'\).  
  
 MFC intenta cargar el archivo DLL de recursos para cada uno de los siguientes idiomas en orden, deteniéndose cuando encuentra uno:  
  
1.  \(Sólo Windows 2000 o posterior\) El idioma de UI predeterminado del usuario actual, que devuelve el API GetUserDefaultUILanguage\(\) de Win32.  
  
2.  \(Solo Windows 2000 o posterior\) El idioma de IU predeterminado del usuario actual, sin ninguna variante de idioma específica \(es decir, ENC \[Inglés canadiense\] se convierte a ENU \[Inglés  de EE.UU.\]\).  
  
3.  El idioma de IU predeterminado del sistema.  En Windows 2000 o posterior, esto se obtiene con la API GetSystemDefaultUILanguage\(\).  En otras plataformas, es el idioma del propio sistema operativo.  
  
4.  El idioma de IU predeterminado del sistema, sin ningún sublenguaje específico.  
  
5.  Un idioma imitador con el código de 3 letras LOC.  
  
 Si MFC no encuentra ningún archivo DLL satélite, utiliza los recursos que contenga la propia aplicación.  
  
 Por ejemplo, imagine que una aplicación LangExample.exe usa MFC y se está ejecutando en un sistema Windows 2000 con varias interfaces de usuario; el idioma de la interfaz de usuario del sistema es ENU \[Inglés  de EE.UU.\] y el idioma de la interfaz de usuario del usuario actual es FRC \[Francés canadiense\].  MFC busca los siguientes archivos DLL en el siguiente orden:  
  
1.  LangExampleFRC.dll \(idioma de IU del usuario\).  
  
2.  LangExampleFRA.dll \(idioma de IU del usuario sin sublenguaje, en este ejemplo, francés \(Francia\).  
  
3.  LangExampleENU.dll \(idioma de IU del sistema\).  
  
4.  LangExampleLOC.dll.  
  
 Si no encuentra ninguno de estos archivos DLL, MFC utiliza los recursos de LangExample.exe.  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)   
 [TN057: Localización de componentes de MFC](../mfc/tn057-localization-of-mfc-components.md)