---
title: Redistribuir una aplicación ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c824dd4ae174a4418c6744e592dd62dc54b9595
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-an-atl-application"></a>Redistribuir una aplicación ATL
A partir de Visual Studio 2012, Active Template Library (ATL) es una biblioteca solo de encabezado. Los proyectos ATL no tienen un vínculo dinámico a la opción de ATL. No se necesita ninguna biblioteca ATL redistribuible.  
  
 Si redistribuye una aplicación ejecutable ATL, debe registrar el archivo .exe (y cualquier control que contenga) ejecutando el siguiente comando:  
  
```  
filename /regserver  
```  
  
 donde `filename` es el nombre del archivo ejecutable.  
  
 En Visual Studio 2010, puede generarse un proyecto ATL para una configuración MinDependency o MinSize. Una configuración MinDependency es lo que se obtiene al establecer la **uso de ATL** propiedad **vínculo estático a ATL** en el **General** página de propiedades y establezca el  **Biblioteca en tiempo de ejecución** propiedad **multiproceso (/ MT)** en el **generación de código** página de propiedades (carpeta C/C ++).  
  
 Una configuración MinSize es lo que se obtiene al establecer la **uso de ATL** propiedad **vínculo dinámico a ATL** en el **General** página de propiedades, o un conjunto el **en tiempo de ejecución Biblioteca** propiedad **DLL multiproceso (/ MD)** en el **generación de código** página de propiedades (carpeta C/C ++).  
  
 MinSize hace que la salida de archivo más pequeño posible, pero requiere que ATL100.dll y Msvcr100.DL (si seleccionó la **DLL multiproceso (/ MD)** opción) están en el equipo de destino. ATL100.dll debe registrarse en el equipo de destino para garantizar que esté presente toda la funcionalidad de ATL. ATL100.dll contiene exportaciones ANSI y Unicode.  
  
 Si compila el proyecto de plantillas ATL u OLE DB para un destino MinDependency, no tendrá que instalar ni registrar ATL100.dll en el equipo de destino, si bien puede obtener una imagen de programa de mayor tamaño.  
  
 Si redistribuye una aplicación ejecutable ATL, debe registrar el archivo .exe (y cualquier control que contenga) ejecutando el siguiente comando:  
  
```  
filename /regserver  
```  
  
 donde `filename` es el nombre del archivo ejecutable.  
  
 Para las aplicaciones de plantillas OLE DB, asegúrese de que el equipo de destino tenga las últimas versiones de los archivos de MDAC (Microsoft Data Access Components). Para obtener más información, consulte [redistribuir archivos de compatibilidad de base de datos](../ide/redistributing-database-support-files.md).  
  
## <a name="see-also"></a>Vea también  
 [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)