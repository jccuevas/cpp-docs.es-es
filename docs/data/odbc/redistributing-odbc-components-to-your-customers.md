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
ms.openlocfilehash: 0d4d3948add665c54be3d3b0596a7a6fc0e414f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212737"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribuir componentes ODBC a los clientes

Si incorpora la funcionalidad de los programas de administrador de ODBC en su aplicación, también debe distribuir a los usuarios los archivos que ejecutan estos programas. Estos archivos ODBC residen en el directorio \OS\System del CD- C++ ROM de visual. El archivo Redistrb. WRI y el contrato de licencia en el mismo directorio contienen una lista de los archivos ODBC que se pueden redistribuir.

Consulte la documentación de los controladores ODBC que desee enviar. Debe determinar qué archivos dll y otros archivos se van a enviar. También debe leer [redistribuir componentes ODBC a los clientes, en](../../data/odbc/redistributing-odbc-components-to-your-customers.md)los que se explica cómo redistribuir los componentes ODBC.

Además, debe incluir otro archivo en la mayoría de los casos. El archivo Odbccr32. dll es la biblioteca de cursores ODBC. Esta biblioteca proporciona a los controladores de nivel 1 la capacidad de desplazamiento hacia delante y hacia atrás. También proporciona la capacidad de admitir instantáneas. Para obtener más información acerca de la biblioteca de cursores ODBC, vea [ODBC: la biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

En los temas siguientes se proporciona más información sobre el uso de ODBC con las clases de base de datos:

- [ODBC: Biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: Configurar un origen de datos ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: Llamar directamente a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Consulte también

[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)<br/>
[Administrador de ODBC](../../data/odbc/odbc-administrator.md)
