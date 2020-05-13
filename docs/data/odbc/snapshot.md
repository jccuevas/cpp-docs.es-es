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
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366904"
---
# <a name="snapshot"></a>Instantánea

Una instantánea es un conjunto de registros que refleja una vista estática de los datos tal como existían en el momento en que se creó la instantánea. Al abrir la instantánea y mover la instantánea a todos los registros, el conjunto de `Requery`registros que contiene y sus valores no cambian hasta que se vuelve a generar la instantánea llamando a .

> [!NOTE]
> Este tema es aplicable a las clases ODBC de MFC. Si utiliza las clases DAO de MFC en lugar de las clases ODBC de MFC, vea [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) para obtener una descripción de conjuntos de registros de tipo instantánea.

Puede crear instantáneas actualizables o de solo lectura con las clases de base de datos. A diferencia de un conjunto de registros dinámicos, una instantánea actualizable no refleja los cambios en los valores de registro realizados por otros usuarios, pero sí refleja las actualizaciones y eliminaciones realizadas por el programa. Los registros agregados a una instantánea no `Requery`se vuelven visibles para la instantánea hasta que se llama a .

> [!TIP]
> Una instantánea es un cursor estático ODBC. Los cursores estáticos no obtienen realmente una fila de datos hasta que se desplaza a ese registro. Para asegurarse de que todos los registros se recuperan inmediatamente, puede desplazarse hasta el final del conjunto de registros y, a continuación, desplazarse hasta el primer registro que desea ver. Tenga en cuenta, sin embargo, que el desplazamiento hasta el final implica una sobrecarga adicional y puede reducir el rendimiento.

Las instantáneas son más valiosas cuando necesita que los datos permanezcan fijos durante las operaciones, como cuando se genera un informe o se realizan cálculos. Aún así, el origen de datos puede diferir considerablemente de la instantánea, por lo que es posible que desee volver a generarla de vez en cuando.

La compatibilidad con instantáneas se basa en la biblioteca de cursores ODBC, que proporciona cursores estáticos y actualizaciones posicionadas (necesarias para la capacidad de actualización) para cualquier controlador de nivel 1. El archivo DLL de la biblioteca de cursores debe cargarse en memoria para esta compatibilidad. Al construir `CDatabase` un objeto `OpenEx` y llamar a su `CDatabase::useCursorLib` función miembro, debe especificar la opción de la *dwOptions* parámetro. Si se `Open` llama a la función miembro, la biblioteca de cursores se carga de forma predeterminada. Si utiliza conjuntos de registros dinámicos en lugar de instantáneas, no desea que se cargue la biblioteca de cursores.

Las instantáneas solo están disponibles si `CDatabase` la biblioteca de cursores ODBC se cargó cuando se construyó el objeto o el controlador ODBC que está utilizando admite cursores estáticos.

> [!NOTE]
> Para algunos controladores ODBC, es posible que las instantáneas (cursores estáticos) no se puedan actualizar. Compruebe la documentación del controlador para los tipos de cursor admitidos y los tipos de simultaneidad que admiten. Para garantizar instantáneas actualizables, asegúrese de cargar la `CDatabase` biblioteca de cursores en la memoria al crear un objeto. Para obtener más información, vea [ODBC: la biblioteca](../../data/odbc/odbc-the-odbc-cursor-library.md)de cursores ODBC .

> [!NOTE]
> Si desea utilizar instantáneas y conjuntos de registros `CDatabase` dinámicos, debe basarlos en dos objetos diferentes (dos conexiones diferentes).

Para obtener más información acerca de las propiedades que las instantáneas comparten con todos los conjuntos de registros, vea [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener más información acerca de ODBC y las instantáneas, incluida la biblioteca de cursores ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Consulte también

[Conectividad de base de datos abierta (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
