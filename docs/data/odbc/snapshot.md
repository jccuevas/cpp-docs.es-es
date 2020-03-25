---
title: Instantánea
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: 62b5952f3052a3248175ce7892b1cf4615f1dd17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212698"
---
# <a name="snapshot"></a>Instantánea

Una instantánea es un conjunto de registros que refleja una vista estática de los datos tal como existían en el momento en que se creó la instantánea. Al abrir la instantánea y pasar a todos los registros, el conjunto de registros que contiene y sus valores no cambian hasta que se vuelve a generar la instantánea llamando a `Requery`.

> [!NOTE]
>  Este tema es aplicable a las clases ODBC de MFC. Si utiliza las clases DAO de MFC en lugar de las clases ODBC de MFC, vea [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open) para obtener una descripción de los conjuntos de registros de tipo Snapshot.

Puede crear instantáneas actualizables o de solo lectura con las clases de base de datos. A diferencia de un conjunto de datos dinámico, una instantánea actualizable no refleja los cambios en los valores de registro realizados por otros usuarios, pero refleja las actualizaciones y eliminaciones realizadas por el programa. Los registros agregados a una instantánea no se vuelven visibles a la instantánea hasta que se llama a `Requery`.

> [!TIP]
>  Una instantánea es un cursor estático de ODBC. Los cursores estáticos no obtienen realmente una fila de datos hasta que se desplaza a ese registro. Para asegurarse de que todos los registros se recuperan inmediatamente, puede desplazarse hasta el final del conjunto de registros y, a continuación, desplazarse hasta el primer registro que desee ver. Sin embargo, tenga en cuenta que, al desplazarse hasta el final, se supone una sobrecarga adicional y se puede reducir el rendimiento.

Las instantáneas son más útiles cuando es necesario que los datos permanezcan fijos durante las operaciones, como cuando se genera un informe o se realizan cálculos. Incluso así, el origen de datos puede diferir considerablemente de la instantánea, por lo que es posible que desee volver a generarlo de vez en cuando.

La compatibilidad con instantáneas se basa en la biblioteca de cursores ODBC, que proporciona cursores estáticos y actualizaciones posicionadas (necesarias para la actualización) para cualquier controlador de nivel 1. La DLL de la biblioteca de cursores se debe cargar en memoria para esta compatibilidad. Al construir un objeto `CDatabase` y llamar a su función miembro `OpenEx`, debe especificar la opción `CDatabase::useCursorLib` del parámetro *dwOptions* . Si se llama a la función miembro `Open`, la biblioteca de cursores se carga de forma predeterminada. Si utiliza dynasets en lugar de instantáneas, no desea que se cargue la biblioteca de cursores.

Las instantáneas solo están disponibles si se cargó la biblioteca de cursores ODBC cuando se construyó el objeto `CDatabase` o si el controlador ODBC que se está utilizando es compatible con cursores estáticos.

> [!NOTE]
>  En algunos controladores ODBC, es posible que las instantáneas (cursores estáticos) no se puedan actualizar. Consulte la documentación del controlador para obtener información sobre los tipos de cursor admitidos y los tipos de simultaneidad que admiten. Para garantizar las instantáneas actualizables, asegúrese de cargar la biblioteca de cursores en memoria cuando cree un objeto de `CDatabase`. Para obtener más información, vea [ODBC: biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Si desea utilizar las instantáneas y los conjuntos de registros dinámicos, debe basarlos en dos objetos de `CDatabase` diferentes (dos conexiones diferentes).

Para obtener más información sobre las propiedades que las instantáneas comparten con todos los conjuntos de registros, vea [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener más información acerca de ODBC e instantáneas, incluida la biblioteca de cursores ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Consulte también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
