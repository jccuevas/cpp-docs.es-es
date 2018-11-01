---
title: Redistribuir componentes ODBC a los clientes
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: cfbe6b2c440f84a4c470255bc964adf6c5145cf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676793"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribuir componentes ODBC a los clientes

Si incorporar la funcionalidad de los programas de administrador de ODBC en su aplicación, también debe distribuir a los usuarios de los archivos que se ejecutan estos programas. Estos archivos ODBC residen en el directorio \OS\System del CD-ROM Visual C++. El archivo Redistrb.wri y el contrato de licencia en el mismo directorio contienen una lista de archivos ODBC que se pueden redistribuir.

Consulte la documentación para los controladores ODBC que se va a enviar. Deberá determinar qué archivos DLL y otros archivos para el envío. También se debe leer [Redistribuir componentes ODBC a los clientes](../../data/odbc/redistributing-odbc-components-to-your-customers.md), que explica cómo redistribuir componentes ODBC.

Además, deberá incluir otro archivo en la mayoría de los casos. El archivo Odbccr32.dll es la biblioteca de cursores ODBC. Esta biblioteca proporciona la capacidad de desplazamiento hacia delante y hacia atrás a controladores de nivel 1. También proporciona la capacidad de admitir instantáneas. Para obtener más información acerca de la biblioteca de cursores ODBC, vea [ODBC: biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

Los temas siguientes proporcionan más información sobre el uso de ODBC con las clases de base de datos:

- [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: Configurar un origen de datos ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: Llamar directamente a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Vea también

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrador de ODBC](../../data/odbc/odbc-administrator.md)