---
title: Conjunto de registros dinámicos
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
ms.openlocfilehash: 21c47546d14d9a121bdd0698fe96eb133dbc44a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395890"
---
# <a name="dynaset"></a>Conjunto de registros dinámicos

Este tema describe los conjuntos de registros dinámicos y explica su [disponibilidad](#_core_availability_of_dynasets).

> [!NOTE]
>  En este tema se aplica a las clases ODBC de MFC, incluido [CRecordset](../../mfc/reference/crecordset-class.md). Para obtener información sobre los conjuntos de registros dinámicos en las clases DAO, vea [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Con DAO, se pueden abrir conjuntos de registros de tipo dinámico.

Tipo dinámico es un conjunto de registros con propiedades dinámicas. Durante su vigencia, un objeto de conjunto de registros en modo dinámico (normalmente denominado dynaset) permanece sincronizado con el origen de datos de la manera siguiente. En un entorno multiusuario, otros usuarios pueden editar o eliminar registros que están en el conjunto de registros dinámicos o agregar registros a la tabla que representa. Registros de la aplicación agrega o elimina el conjunto de registros se reflejan en el conjunto de registros dinámicos. Los registros que otros usuarios se agregan a la tabla no se reflejarán en el conjunto de registros dinámicos hasta que se vuelve a generar el conjunto de registros dinámicos mediante una llamada a su `Requery` función miembro. Cuando otros usuarios eliminan registros, código MFC omite las eliminaciones en el conjunto de registros. Cambios de edición de otros usuarios a los registros existentes se reflejan en el conjunto de registros dinámicos en cuanto se desplaza al registro afectado.

De forma similar, la modificación que realice en los registros de tipo dinámico se refleja en conjuntos de registros dinámicos en uso por otros usuarios. Registros que se agregan no se reflejan en conjuntos de registros dinámicos de otros usuarios hasta que volver a consultar sus conjuntos de registros dinámicos. Elimina los registros se marcan como "eliminadas" en los conjuntos de registros de otros usuarios. Si tiene varias conexiones a la misma base de datos (varias `CDatabase` objetos), conjuntos de registros asociados con esas conexiones tienen el mismo estado como los conjuntos de registros de otros usuarios.

Conjuntos de registros dinámicos son más útiles cuando los datos deben ser dinámicos, como (por ejemplo) en un sistema de reserva de la compañía aérea.

> [!NOTE]
> Para usar conjuntos de registros dinámicos, debe tener un controlador ODBC para el origen de datos que admite conjuntos de registros dinámicos y no se debe cargar la biblioteca de cursores ODBC. Para obtener más información, consulte [disponibilidad de conjuntos de registros dinámicos](#_core_availability_of_dynasets).

Para especificar que un conjunto de registros es de tipo dinámico, pase `CRecordset::dynaset` como primer parámetro para el `Open` función de miembro del objeto de conjunto de registros.

> [!NOTE]
> Para conjuntos de registros dinámicos actualizables, el controlador ODBC debe admitir instrucciones de actualización por posición o el `::SQLSetPos` función de la API de ODBC. Si se admiten ambas, MFC utiliza `::SQLSetPos` para mejorar la eficacia.

##  <a name="_core_availability_of_dynasets"></a> Disponibilidad de los conjuntos de registros dinámicos

Las clases de base de datos MFC admiten conjuntos de registros dinámicos si se cumplen los requisitos siguientes:

- La biblioteca de cursores ODBC DLL no debe estar en uso para este origen de datos.

   Si se usa la biblioteca de cursores, enmascara alguna funcionalidad del controlador ODBC subyacente que es necesario para la compatibilidad de tipo dinámico. Si desea utilizar conjuntos de registros dinámicos (y el controlador ODBC tiene la funcionalidad necesaria para conjuntos de registros dinámicos, como se describe en el resto de esta sección), puede hacer que MFC no cargue la biblioteca de cursores cuando creas un `CDatabase` objeto. Para obtener más información, consulte [ODBC](../../data/odbc/odbc-basics.md) y [OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [abierto](../../mfc/reference/cdatabase-class.md#open) función miembro de clase `CDatabase`.

   En la terminología ODBC, conjuntos de registros dinámicos y las instantáneas se denominan cursores. Un cursor es un mecanismo utilizado para realizar el seguimiento de su posición en un conjunto de registros.

- El controlador ODBC para el origen de datos debe admitir los cursores dinámicos.

   Los cursores controlados por administración los datos de una tabla mediante la obtención y almacenar un conjunto de claves. Las claves se utilizan para obtener los datos actuales de la tabla cuando el usuario se desplaza a un registro concreto. Para determinar si el controlador proporciona esta compatibilidad, llame a la `::SQLGetInfo` función API de ODBC con el *SQL_SCROLL_OPTIONS* parámetro.

   Si intenta abrir un conjunto de registros dinámicos sin compatibilidad con conjuntos de claves, obtendrá un `CDBException` con el código de retorno valor AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED.

- El controlador ODBC para el origen de datos debe admitir obtención extendida.

   Obtención extendida es la capacidad de desplazarse hacia atrás, así como reenviar a través de los registros resultantes de la consulta SQL. Para determinar si el controlador admite esta capacidad, llame a la `::SQLGetFunctions` función API de ODBC con el *SQL_API_SQLEXTENDEDFETCH* parámetro.

Si desea conjuntos de registros dinámicos actualizables (o instantáneas, de hecho), el controlador ODBC también debe admitir la `::SQLSetPos` actualizaciones por posición o función de la API de ODBC. El `::SQLSetPos` función permite MFC actualizar el origen de datos sin enviar instrucciones SQL. Si esta compatibilidad está disponible, MFC utiliza antes que hacer actualizaciones mediante SQL. Para determinar si el controlador admite `::SQLSetPos`, llame a `::SQLGetInfo` con el *SQL_POS_OPERATIONS* parámetro.

Actualizaciones por posición utilizan la sintaxis SQL (del formulario **WHERE CURRENT OF** \<cursorname >) para identificar una fila determinada en la tabla del origen de datos. Para determinar si el controlador admite las actualizaciones posicionadas, llame a `::SQLGetInfo` con el *SQL_POSITIONED_STATEMENTS* parámetro.

Por lo general, conjuntos de registros dinámicos MFC (pero no sólo hacia delante) necesita un controlador ODBC con la conformidad de la API de nivel 2. Si el controlador para el origen de datos es compatible con el conjunto de API de nivel 1, todavía puede usar tanto instantáneas actualizables y de solo lectura y conjuntos de registros solo hacia delante, pero no los dynasets. Sin embargo, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite obtención extendida y los cursores dinámicos. Para obtener más información acerca de los niveles de compatibilidad de ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).

> [!NOTE]
> Si desea utilizar instantáneas y conjuntos de registros dinámicos, se debe basar en dos diferentes `CDatabase` objetos (dos conexiones distintas).

A diferencia de instantáneas, que usan almacenamiento intermedio mantenido por la biblioteca de cursores ODBC, conjuntos de registros dinámicos obtienen un registro directamente desde el origen de datos tan pronto como se desplaza a él. Esto evita que los registros seleccionados originalmente por el conjunto de registros dinámicos sincronizado con el origen de datos.

Para obtener una lista de controladores ODBC incluidos en esta versión de Visual C++ y para obtener información acerca de cómo obtener controladores adicionales, consulte [lista de controladores ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="see-also"></a>Vea también

[Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)