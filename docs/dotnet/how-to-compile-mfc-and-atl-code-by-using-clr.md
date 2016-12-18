---
title: "C&#243;mo: Compilar c&#243;digo de MFC y ATL mediante /clr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr (opción del compilador) [C++], compilar código de MFC y ATL"
  - "ATL [C++], interoperabilidad"
  - "DLL de extensión [C++], /clr (opción del compilador)"
  - "interoperabilidad [C++], /clr (opción del compilador)"
  - "interoperabilidad [C++], /clr (opción del compilador)"
  - "MFC [C++], interoperabilidad"
  - "ensamblados mixtos [C++], código ATL"
  - "ensamblados mixtos [C++], código MFC"
  - "DLLs regulares [C++], /clr (opción del compilador)"
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Compilar c&#243;digo de MFC y ATL mediante /clr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo compilar los programas MFC y ATL existentes para utilizarlos en Common Language Runtime.  
  
### Para compilar un ejecutable de MFC o un archivo DLL estándar mediante \/clr  
  
1.  Haga clic con el botón secundario en el proyecto en el **Explorador de soluciones** y, a continuación, haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo **Propiedades del proyecto**, expanda el nodo situado junto a **Propiedades de configuración** y seleccione **General**.  En el panel derecho, en **Valores predeterminados del proyecto**, establezca **Compatibilidad con Common Language Runtime** en **Compatible con Common Language Runtime \(\/clr\)**.  
  
     En el mismo panel, asegúrese de que la opción **Uso de MFC** esté establecida en **Utilizar MFC en un archivo DLL compartido**.  
  
3.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  Asegúrese de que la opción **Formato de la información de depuración** esté establecida en **Base de datos de programa \(\/Zi\)** \(y no en **\/ZI**\).  
  
4.  Seleccione el nodo **Generación de código**.  Establezca **Habilitar recompilación mínima** en **No \(\/Gm\-\)**.  Establezca también **Comprobaciones básicas en tiempo de ejecución** en **Predeterminado**.  
  
5.  En **Propiedades de configuración**, seleccione **C\/C\+\+** y, a continuación, **Generación de código**.  Asegúrese de que la opción **Biblioteca en tiempo de ejecución** esté establecida en **DLL de depuración multiproceso \(\/MDd\)** o **DLL multiproceso \(\/MD\)**.  
  
6.  En Stdafx.h, agregue la línea siguiente.  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### Para compilar un archivo DLL de extensión de MFC mediante \/clr  
  
1.  Siga los pasos descritos en "Para compilar un ejecutable de MFC o un archivo DLL estándar mediante \/clr".  
  
2.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **Encabezados precompilados**.  Establezca **Crear o utilizar encabezado precompilado** en **No utilizar encabezados precompilados**.  
  
     Como alternativa, en el **Explorador de soluciones**, haga clic con el botón secundario en Stdafx.cpp y, a continuación, haga clic en **Propiedades**.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  Establezca **Compilar con compatibilidad para Common Language Runtime** en **No es compatible con Common Language Runtime**.  
  
3.  Para el archivo que contiene DllMain y cualquier objeto que invoque, en el **Explorador de soluciones**, haga clic con el botón secundario en el archivo y, a continuación, haga clic en **Propiedades**.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  En el panel derecho, en **Valores predeterminados del proyecto**, establezca **Compilar con compatibilidad para Common Language Runtime** en **No es compatible con Common Language Runtime**.  
  
### Para compilar un ejecutable de ATL mediante \/clr  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
2.  En el cuadro de diálogo **Propiedades del proyecto**, expanda el nodo situado junto a **Propiedades de configuración** y seleccione **General**.  En el panel derecho, en **Valores predeterminados del proyecto**, establezca **Compatibilidad con Common Language Runtime** en **Compatible con Common Language Runtime \(\/clr\)**.  
  
3.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  Asegúrese de que la opción **Formato de la información de depuración** esté establecida en **Base de datos de programa \(\/Zi\)** \(y no en **\/ZI**\).  
  
4.  Seleccione el nodo **Generación de código**.  Establezca **Habilitar recompilación mínima** en **No \(\/Gm\-\)**.  Establezca también **Comprobaciones básicas en tiempo de ejecución** en **Predeterminado**.  
  
5.  En **Propiedades de configuración**, seleccione **C\/C\+\+** y, a continuación, **Generación de código**.  Asegúrese de que la opción **Biblioteca en tiempo de ejecución** esté establecida en **DLL de depuración multiproceso \(\/MDd\)** o **DLL multiproceso \(\/MD\)**.  
  
6.  Para cada archivo generado por MIDL \(archivos de C\), haga clic con el botón secundario del mouse en el archivo en el **Explorador de soluciones** y, a continuación, haga clic en **Propiedades**.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  Establezca **Compilar con compatibilidad para Common Language Runtime** en **No es compatible con Common Language Runtime**.  
  
### Para compilar un archivo DLL de ATL mediante \/clr  
  
1.  Siga los pasos descritos en "Para compilar un ejecutable de ATL mediante \/clr".  
  
2.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **Encabezados precompilados**.  Establezca **Crear o utilizar encabezado precompilado** en **No utilizar encabezados precompilados**.  
  
     Como alternativa, en el **Explorador de soluciones**, haga clic con el botón secundario en Stdafx.cpp y, a continuación, haga clic en **Propiedades**.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  Establezca **Compilar con compatibilidad para Common Language Runtime** en **No es compatible con Common Language Runtime**.  
  
3.  Para el archivo que contiene DllMain y cualquier objeto que invoque, en el **Explorador de soluciones**, haga clic con el botón secundario en el archivo y, a continuación, haga clic en **Propiedades**.  En **Propiedades de configuración**, expanda el nodo situado junto a **C\/C\+\+** y seleccione **General**.  En el panel derecho, en **Valores predeterminados del proyecto**, establezca **Compilar con compatibilidad para Common Language Runtime** en **No es compatible con Common Language Runtime**.  
  
## Vea también  
 [Ensamblados mixtos \(nativos y administrados\)](../dotnet/mixed-native-and-managed-assemblies.md)