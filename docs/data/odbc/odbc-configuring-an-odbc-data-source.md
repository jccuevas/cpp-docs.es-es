---
title: 'ODBC: Configurar un origen de datos ODBC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 93b2158005b7cd31fc6a3710812d54a3968ee014
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="odbc-configuring-an-odbc-data-source"></a>ODBC: Configurar un origen de datos ODBC
Para usar un [origen de datos](../../data/odbc/data-source-odbc.md) con una aplicación que haya desarrollado, debe usar el Administrador de ODBC para configurarlo. El Administrador de ODBC realiza un seguimiento de los orígenes de datos disponibles y su información de conexión en el registro de Windows. Utilice el Administrador de ODBC para agregar, modificar y eliminar orígenes de datos en el **orígenes de datos** cuadro de diálogo y para agregar y eliminar controladores ODBC.  
  
> [!NOTE]
>  Esta información se aplica cuando se utilizan clases de objeto de acceso a datos (DAO) de MFC para tener acceso a ODBC y si utiliza las clases ODBC de MFC.  
  
 El Administrador de ODBC se instala automáticamente con la compatibilidad con la base de datos de biblioteca de Microsoft Foundation Classes (MFC). Para obtener más información sobre el programa del Administrador de ODBC, vea [Administrador ODBC](../../data/odbc/odbc-administrator.md) y el sistema de Ayuda de referencia de API de ODBC en línea.  
  
 Para obtener información sobre cómo escribir programas de instalación y administración ODBC para aplicaciones de base de datos MFC,[Nota técnica 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)   
 [ODBC: Llamar directamente a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)