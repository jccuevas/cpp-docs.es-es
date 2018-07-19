---
title: Redistribuir componentes ODBC a los clientes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0427228b8fb3e852cf1d9ee66a10c9290b860b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090229"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribuir componentes ODBC a los clientes
Si se incorpora la funcionalidad de los programas de administrador de ODBC en la aplicación, también debe distribuir a los usuarios los archivos que se ejecutan estos programas. Estos archivos ODBC residen en el directorio \OS\System del CD-ROM Visual C++. El archivo Redistrb.wri y el contrato de licencia en el mismo directorio contienen una lista de los archivos ODBC que se pueden redistribuir.  
  
 Consulte la documentación para los controladores ODBC que se va a enviar. Debe determinar qué archivos DLL y otros archivos para enviar. También debe leer [Redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md), que explica cómo redistribuir los componentes de ODBC.  
  
 Además, debe incluir otro archivo en la mayoría de los casos. El archivo Odbccr32.dll es la biblioteca de cursores ODBC. Esta biblioteca proporciona a los controladores de nivel 1 la capacidad de desplazamiento hacia delante y hacia atrás. También proporciona la capacidad de admitir instantáneas. Para obtener más información acerca de la biblioteca de cursores ODBC, vea [ODBC: biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
 Los temas siguientes proporcionan más información sobre el uso de ODBC con las clases de base de datos:  
  
-   [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
-   [ODBC: Configurar un origen de datos ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)  
  
-   [ODBC: Llamar directamente a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)   
 [Administrador de ODBC](../../data/odbc/odbc-administrator.md)