---
title: Redistribuir archivos de compatibilidad con bases de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing database support files
- database support files [C++], redistributing
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55888388158cbe005709cbe8a4989071213b5c77
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195733"
---
# <a name="redistributing-database-support-files"></a>Redistribuir archivos de compatibilidad con bases de datos
Puede redistribuir archivos de compatibilidad para objetos de acceso a datos (DAO) y para las tecnologías de base de datos en el Kit de desarrollo de software (SDK) de Microsoft Data Access.  
  
## <a name="installing-dao-support-files"></a>Instalar archivos de compatibilidad DAO  
 Para obtener la versión más reciente de DAO, vea el [artículo 239114: Cómo obtener el Service Pack más reciente para el motor de base de datos Microsoft Jet 4.0](http://go.microsoft.com/fwlink/p/?linkid=198014) en el sitio web de Soporte de Microsoft.  
  
## <a name="installing-microsoft-data-access-sdk-support-files"></a>Instalar los archivos de compatibilidad del Microsoft Data Access SDK  
 Use Mdac_typ.exe para instalar los archivos de compatibilidad con ODBC, OLE DB, ActiveX Data Objects (ADO) y Remote Data Services (RDS). Mdac_typ.exe se encuentra en la carpeta ..\WCU\MDAC28\ del disco de instalación de Visual Studio. También puede descargar Mdac_typ.exe desde el sitio web del [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/p/?linkid=198015).  
  
 Para obtener más información, en el sitio web de [MSDN](http://go.microsoft.com/fwlink/p/?linkid=198016), busque "Redistribuir MDAC 2.8 SP1". Si usa los proyectos de instalación de Visual Studio para implementar la aplicación, vea [Implementación y dependencias](https://msdn.microsoft.com/49e9b84d-bd6a-4388-b9ac-46ea79cf0733).  
  
## <a name="see-also"></a>Vea también  
 [Redistribuir archivos de Visual C++](../ide/redistributing-visual-cpp-files.md)