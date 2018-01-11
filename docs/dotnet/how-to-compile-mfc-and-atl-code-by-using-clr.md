---
title: "Cómo: compilar código ATL y MFC mediante clr-| Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f03e324cf4f88d47232cba5e15ec65181af91feb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Cómo: Compilar código de MFC y ATL mediante /clr
Este tema describe cómo compilar programas MFC y ATL existentes para tener como destino el Common Language Runtime.  
  
### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Para compilar una DLL de MFC MFC normales o ejecutable con /clr  
  
1.  Haga clic en el proyecto en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades**.  
  
2.  En el **propiedades del proyecto** cuadro de diálogo, expanda el nodo junto a **propiedades de configuración** y seleccione **General**. En el panel derecho, en **valores predeterminados del proyecto**, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**.  
  
     En el mismo panel, asegúrese de que **uso de MFC** está establecido en **utilizar MFC en un archivo DLL compartido**.  
  
3.  En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. Asegúrese de que **formato de información de depuración** está establecido en **/Zi de base de datos de programa** (no **/Zi**).  
  
4.  Seleccione el **generación de código** nodo. Establecer **habilitar recompilación mínima** a **No (/ Gm-)**. Establecer **comprobaciones en tiempo de ejecución básicas** a **predeterminado**.  
  
5.  En **propiedades de configuración**, seleccione **C/C++** y, a continuación, **generación de código**. Asegúrese de que **biblioteca en tiempo de ejecución** está establecido en **DLL de depuración multiproceso (/ MDd)** o **DLL multiproceso (/ MD)**.  
  
6.  En Stdafx.h, agregue la siguiente línea.  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Para compilar un archivo DLL de extensión MFC con /clr  
  
1.  Siga los pasos descritos en "To compila una DLL de MFC MFC normales o ejecutable con/CLR".  
  
2.  En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **encabezados precompilados**. Establecer **crear o utilizar encabezado precompilado** a **no utilizar encabezados precompilados**.  
  
     Como alternativa, en **el Explorador de soluciones**, haga clic en Stdafx.cpp y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. Establecer **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.  
  
3.  Para el archivo que contiene DllMain y cualquier aplicación llama, en **el Explorador de soluciones**, haga clic en el archivo y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. En el panel derecho, en **valores predeterminados del proyecto**, establezca **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.  
  
### <a name="to-compile-an-atl-executable-by-using-clr"></a>Para compilar un ejecutable ATL mediante /clr  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**.  
  
2.  En el **propiedades del proyecto** cuadro de diálogo, expanda el nodo junto a **propiedades de configuración** y seleccione **General**. En el panel derecho, en **valores predeterminados del proyecto**, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**.  
  
3.  En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. Asegúrese de que **formato de información de depuración** está establecido en **/Zi de base de datos de programa** (no **/Zi**).  
  
4.  Seleccione el **generación de código** nodo. Establecer **habilitar recompilación mínima** a **No (/ Gm-)**. Establecer **comprobaciones en tiempo de ejecución básicas** a **predeterminado**.  
  
5.  En **propiedades de configuración**, seleccione **C/C++** y, a continuación, **generación de código**. Asegúrese de que **biblioteca en tiempo de ejecución** está establecido en **DLL de depuración multiproceso (/ MDd)** o **DLL multiproceso (/ MD)**.  
  
6.  Para cada archivo generados por MIDL (archivos de C), haga clic en el archivo en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. Establecer **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.  
  
### <a name="to-compile-an-atl-dll-by-using-clr"></a>Para compilar una DLL de ATL mediante /clr  
  
1.  Siga los pasos descritos en la sección "para compilar un ejecutable de ATL mediante /clr".  
  
2.  En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **encabezados precompilados**. Establecer **crear o utilizar encabezado precompilado** a **no utilizar encabezados precompilados**.  
  
     Como alternativa, en **el Explorador de soluciones**, haga clic en Stdafx.cpp y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. Establecer **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.  
  
3.  Para el archivo que contiene DllMain y cualquier aplicación llama, en **el Explorador de soluciones**, haga clic en el archivo y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C/C++** y seleccione **General**. En el panel derecho, en **valores predeterminados del proyecto**, establezca **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)