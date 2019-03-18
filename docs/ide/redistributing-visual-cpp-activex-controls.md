---
title: Redistribuir controles ActiveX de Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: fb4ef7b58f5ef596ac6484761ab891ceb8bb85ad
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744644"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribuir controles ActiveX de Visual C++

Visual C++ 6.0 proporciona controles ActiveX que se pueden usar en las aplicaciones que después se van a redistribuir. Estos controles ya no se incluyen en Visual C++. Según los contratos de licencia para Visual C++ 6.0, puede redistribuir estos controles con las aplicaciones desarrolladas en Visual C++.

> [!NOTE]
>  Visual C++ 6.0 ya no recibe soporte de Microsoft.

Para obtener una lista de los controles ActiveX de Visual C++ 6.0 redistribuibles, vea Common\Redist\Redist.txt en el disco 1 del CD del producto de Visual C++ 6.0.

Al distribuir aplicaciones, debe instalar y registrar el archivo .ocx del control ActiveX (mediante Regsvr32.exe). Además, debe asegurarse de que el equipo de destino tiene las versiones actuales de los archivos de sistema siguientes (un asterisco indica que el archivo se tiene que registrar):

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

Si estos archivos DLL no están disponibles en el sistema de destino, se deben actualizar mediante el mecanismo indicado para actualizar el sistema operativo correspondiente. Puede descargar los Service Pack más recientes para los sistemas operativos de Windows de [http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com).

Cuando se usa un control ActiveX que se conecta a una base de datos, también se debe replicar el nombre del origen de datos en el equipo de destino. Esto se puede hacer mediante programación con funciones como `ConfigDSN`.

Algunos controles ActiveX redistribuibles tienen dependencias adicionales. Para cada archivo .ocx de la carpeta Os\System del CD de producto de Visual C++ 6.0, también hay un archivo .dep. Por cada archivo .ocx que quiera redistribuir, busque una o más entradas USES en el archivo .dep correspondiente. Si aparece un archivo, debe asegurarse de que esté en el equipo de destino. Los archivos DLL que admitan directamente un archivo .ocx tienen que registrarse. (Para que Regsvr32.exe funcione correctamente, el equipo de destino debe contener primero todos los archivos DLL que el control carga de manera estática). Además, si un archivo DLL que aparece como una dependencia tiene también un archivo .dep en la carpeta Os\System del CD de Visual C++ 6.0, también debe investigar las entradas USES en ese archivo.

## <a name="see-also"></a>Vea también

[Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)
