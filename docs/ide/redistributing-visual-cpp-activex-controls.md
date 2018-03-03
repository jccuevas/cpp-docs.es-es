---
title: Redistribuir controles ActiveX de Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c520d365a259c36baab8edeb9049aab9ac89925a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribuir controles ActiveX de Visual C++
Visual C++ 6.0 proporciona controles ActiveX que puede usar en aplicaciones que se va a redistribuir. Estos controles no se incluyen en Visual C++. Según los contratos de licencia para Visual C++ 6.0, puede redistribuir estos controles con las aplicaciones desarrolladas en Visual C++.  
  
> [!NOTE]
>  Visual C++ 6.0 ya no es compatible con Microsoft.  
  
 Para obtener una lista de los controles ActiveX de Visual C++ 6.0 redistribuibles, vea Common\Redist\Redist.txt en el disco 1 del CD del producto de Visual C++ 6.0.  
  
 Al distribuir aplicaciones, debe instalar y registrar el archivo .ocx del control ActiveX (con Regsvr32.exe). Además, debe asegurarse de que el equipo de destino tiene las versiones actuales de los siguientes archivos de sistema (un asterisco indica que el archivo tiene que registrar):  
  
-   Asycfilt.dll  
  
-   Comcat.dll *  
  
-   Oleaut32.dll *  
  
-   OLEPRO32.dll *  
  
-   Stdole2.tlb  
  
 Si estos archivos DLL no están disponibles en el sistema de destino, debe obtener una copia actualizada con el mecanismo indicado para actualizar el sistema operativo correspondiente. Puede descargar el service Pack más recientes para los sistemas operativos de Windows de [http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com).  
  
 Si su aplicación utiliza uno de los controles ActiveX que se conecta a una base de datos, debe tener los componentes de acceso de datos de Microsoft (MDAC) instalado en el sistema de destino. Para obtener más información, consulte [redistribuir archivos de compatibilidad de base de datos](../ide/redistributing-database-support-files.md).  
  
 Cuando se utiliza un control ActiveX que se conecta a una base de datos, debe replicarse el nombre del origen de datos en el equipo de destino. Puede hacerlo mediante programación con funciones como `ConfigDSN`.  
  
 Algunos controles ActiveX redistribuibles poseen dependencias adicionales. Para cada archivo .ocx de la carpeta Os\System del CD de producto de Visual C++ 6.0, también hay un archivo DEP. Por cada archivo .ocx que desea redistribuir, busque uno o más entradas USES en el archivo DEP. correspondiente. Si aparece un archivo, debe asegurarse de que el archivo está en el equipo de destino. Los archivos DLL auxiliares directamente un archivo .ocx tienen que ser registrados. (Para que Regsvr32.exe funcione correctamente, el equipo de destino debe contener todas las DLL que carga el control estáticamente.) Además, si un archivo DLL que aparece como una dependencia tiene también un archivo DEP. en la carpeta Os\System del CD de Visual C++ 6.0, se debe investigar para entradas USES en dicho archivo.  
  
## <a name="see-also"></a>Vea también  
 [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)