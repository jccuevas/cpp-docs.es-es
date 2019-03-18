---
title: Filtrar Compilar código ATL y MFC mediante - clr
ms.custom: get-started-article
ms.date: 11/04/2016
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
ms.openlocfilehash: 9a24e82787eb0fce8ff668843e73de9f2d05e1ad
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751614"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Filtrar Compilar código By Using ATL y MFC/CLR

En este tema se describe cómo compilar programas MFC y ATL existentes para tener como destino Common Language Runtime.

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Para compilar una DLL de MFC MFC normales o ejecutable con/CLR

1. Haga clic en el proyecto en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades**.

1. En el **las propiedades del proyecto** diálogo cuadro, expanda el nodo junto a **propiedades de configuración** y seleccione **General**. En el panel derecho, bajo **valores predeterminados del proyecto**, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**.

   En el mismo panel, asegúrese de que **uso de MFC** está establecido en **utilizar MFC en un archivo DLL compartido**.

1. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. Asegúrese de que **formato de información de depuración** está establecido en **/Zi de base de datos de programa** (no **/Zi**).

1. Seleccione el **generación de código** nodo. Establecer **habilitar recompilación mínima** a **No (/ Gm-)**. También establece **comprobaciones en tiempo de ejecución básicas** a **predeterminado**.

1. En **propiedades de configuración**, seleccione **C o C++** y, a continuación, **generación de código**. Asegúrese de que **biblioteca en tiempo de ejecución** está establecida en **DLL de depuración multiproceso (/ MDd)** o **DLL multiproceso (/ MD)**.

1. En Stdafx.h, agregue la siguiente línea.

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Para compilar un archivo DLL de extensión MFC con/CLR

1. Siga los pasos descritos en "To compila una DLL de MFC MFC normales o ejecutable con/CLR".

1. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **encabezados precompilados**. Establecer **crear o utilizar encabezado precompilado** a **no utilizar encabezados precompilados**.

   Como alternativa, en **el Explorador de soluciones**, haga clic en Stdafx.cpp y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. Establecer **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.

1. En el archivo que contiene DllMain y cualquier otra cosa llamadas, en **el Explorador de soluciones**, haga clic en el archivo y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. En el panel derecho, bajo **valores predeterminados del proyecto**, establezca **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.

### <a name="to-compile-an-atl-executable-by-using-clr"></a>Para compilar un ejecutable ATL mediante /clr

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**.

1. En el **las propiedades del proyecto** diálogo cuadro, expanda el nodo junto a **propiedades de configuración** y seleccione **General**. En el panel derecho, bajo **valores predeterminados del proyecto**, establezca **compatible con Common Language Runtime** a **compatible con Common Language Runtime (/ clr)**.

1. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. Asegúrese de que **formato de información de depuración** está establecido en **/Zi de base de datos de programa** (no **/Zi**).

1. Seleccione el **generación de código** nodo. Establecer **habilitar recompilación mínima** a **No (/ Gm-)**. También establece **comprobaciones en tiempo de ejecución básicas** a **predeterminado**.

1. En **propiedades de configuración**, seleccione **C o C++** y, a continuación, **generación de código**. Asegúrese de que **biblioteca en tiempo de ejecución** está establecida en **DLL de depuración multiproceso (/ MDd)** o **DLL multiproceso (/ MD)**.

1. Para cada archivo generado por MIDL (archivos de C), haga clic en el archivo en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. Establecer **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.

### <a name="to-compile-an-atl-dll-by-using-clr"></a>Para compilar una DLL de ATL mediante /clr

1. Siga los pasos descritos en la sección "para compilar un ejecutable ATL mediante /clr".

1. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **encabezados precompilados**. Establecer **crear o utilizar encabezado precompilado** a **no utilizar encabezados precompilados**.

   Como alternativa, en **el Explorador de soluciones**, haga clic en Stdafx.cpp y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. Establecer **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.

1. En el archivo que contiene DllMain y cualquier otra cosa llamadas, en **el Explorador de soluciones**, haga clic en el archivo y, a continuación, haga clic en **propiedades**. En **propiedades de configuración**, expanda el nodo junto a **C o C++** y seleccione **General**. En el panel derecho, bajo **valores predeterminados del proyecto**, establezca **compilar con compatibilidad con Common Language Runtime** a **soporte técnico No Common Language Runtime**.

## <a name="see-also"></a>Vea también

[Ensamblados mixtos (nativos y administrados)](../dotnet/mixed-native-and-managed-assemblies.md)
