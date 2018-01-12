---
title: "Conjunto de registros dinámicos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets, dynasets
- ODBC cursor library [ODBC], dynasets
- keyset-driven cursors in dynasets
- cursors [ODBC], keyset-driven cursors in dynasets
- cursor library [ODBC], dynaset availability
- recordsets [C++], dynasets
- dynasets
ms.assetid: 2867e6be-208e-4fe7-8bbe-b8697cb1045c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f0f2f7ddd4a1b4021dfff8d533bb81acd84129a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dynaset"></a>Conjunto de registros dinámicos
Este tema describe los conjuntos de registros dinámicos y explica su [disponibilidad](#_core_availability_of_dynasets).  
  
> [!NOTE]
>  En este tema se aplica a las clases ODBC de MFC, incluidos los [CRecordset](../../mfc/reference/crecordset-class.md). Para obtener información acerca de conjuntos de registros dinámicos en las clases DAO, vea [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md). Con DAO, puede abrir conjuntos de registros de tipo dinámico.  
  
 Un conjunto de registros dinámicos es un conjunto de registros con propiedades dinámicas. Durante su duración, un objeto de conjunto de registros en modo de conjunto de registros dinámicos (que normalmente se denominan conjuntos de registros dinámicos) permanece sincronizado con el origen de datos de la manera siguiente. En un entorno multiusuario, otros usuarios pueden editar o eliminar registros que están en el conjunto de registros dinámicos o agregar registros a la tabla que representa el conjunto de registros dinámicos. Registros de la aplicación agrega o quita el conjunto de registros se reflejan en el conjunto de registros dinámicos. Los registros que otros usuarios se agregan a la tabla no se reflejarán en el conjunto de registros dinámicos hasta que se vuelve a generar el conjunto de registros dinámicos mediante una llamada a su **Requery** función miembro. Cuando otros usuarios eliminan registros, código MFC omite las eliminaciones en el conjunto de registros. Cambios de edición de otros usuarios en los registros existentes se reflejan en el conjunto de registros dinámicos en cuanto se desplaza al registro afectado.  
  
 De forma similar, las modificaciones que se realice en los registros de un conjunto de registros dinámicos se reflejan en conjuntos de registros dinámicos en uso por otros usuarios. Registros que se agregan no se reflejan en conjuntos de registros dinámicos de otros usuarios hasta que realicen una nueva consulta sus conjuntos de registros dinámicos. Elimina los registros se marcan como "eliminados" en los conjuntos de registros de otros usuarios. Si tiene varias conexiones a la misma base de datos (varios `CDatabase` objetos), conjuntos de registros asociados a dichas conexiones tienen el mismo estado como los conjuntos de registros de otros usuarios.  
  
 Conjuntos de registros dinámicos son más útiles cuando los datos deben ser dinámicos, como (por ejemplo) en un sistema de reserva airline.  
  
> [!NOTE]
>  Para usar conjuntos de registros dinámicos, debe tener un controlador ODBC para el origen de datos que es compatible con conjuntos de registros dinámicos y no se debe cargar la biblioteca de cursores ODBC. Para obtener más información, consulte [disponibilidad de conjuntos de registros dinámicos](#_core_availability_of_dynasets).  
  
 Para especificar que un conjunto de registros es un conjunto de registros dinámicos, pasar **CRecordset:: dynaset** como primer parámetro a la **abiertos** función miembro de su objeto de conjunto de registros.  
  
> [!NOTE]
>  Para conjuntos de registros dinámicos actualizables, el controlador ODBC debe admitir instrucciones de actualización por posición o el **:: SQLSetPos** función de la API de ODBC. Si se admiten ambas, MFC utiliza **:: SQLSetPos** para mejorar la eficacia.  
  
##  <a name="_core_availability_of_dynasets"></a>Disponibilidad de los conjuntos de registros dinámicos  
 Las clases de base de datos MFC admiten conjuntos de registros dinámicos si se cumplen los requisitos siguientes:  
  
-   La biblioteca de cursores ODBC DLL no debe estar en uso para este origen de datos.  
  
     Si se utiliza la biblioteca de cursores, enmascara parte de la funcionalidad del controlador ODBC subyacente que es necesario para la compatibilidad de conjunto de registros dinámicos. Si desea utilizar conjuntos de registros dinámicos (y el controlador ODBC posee la funcionalidad necesaria para conjuntos de registros dinámicos, como se describe en el resto de esta sección), puede hacer que MFC no cargue la biblioteca de cursores al crear un `CDatabase` objeto. Para obtener más información, consulte [ODBC](../../data/odbc/odbc-basics.md) y [OpenEx](../../mfc/reference/cdatabase-class.md#openex) o [abiertos](../../mfc/reference/cdatabase-class.md#open) función miembro de clase `CDatabase`.  
  
     En la terminología ODBC, conjuntos de registros dinámicos y las instantáneas se denominan cursores. Un cursor es un mecanismo utilizado para realizar el seguimiento de su posición en un conjunto de registros.  
  
-   El controlador ODBC para el origen de datos debe admitir cursores dinámicos.  
  
     Los cursores controlados por conjunto de claves administran datos de una tabla mediante la obtención y almacenar un conjunto de claves. Las claves se utilizan para obtener datos actuales de la tabla cuando el usuario se desplaza a un registro concreto. Para determinar si el controlador proporciona esta compatibilidad, llame a la **:: SQLGetInfo** función de la API de ODBC con el **SQL_SCROLL_OPTIONS** parámetro.  
  
     Si intenta abrir un conjunto de registros dinámicos sin compatibilidad con conjunto de claves, obtendrá un `CDBException` con el valor de código de retorno **AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED**.  
  
-   El controlador ODBC para el origen de datos debe admitir obtención extendida.  
  
     Obtención extendida es la capacidad para desplazarse hacia atrás, así como reenviar a través de los registros resultantes de la consulta SQL. Para determinar si el controlador es compatible con esta capacidad, llame a la **:: SQLGetFunctions** función de la API de ODBC con el **SQL_API_SQLEXTENDEDFETCH** parámetro.  
  
 Si se desean conjuntos de registros dinámicos actualizables (o instantáneas, con este propósito), el controlador ODBC también debe admitir la **:: SQLSetPos** función de la API de ODBC o actualizaciones por posición. El **:: SQLSetPos** función permite a MFC actualizar el origen de datos sin enviar instrucciones SQL. Si esta compatibilidad está disponible, MFC prefiere utilizarla antes que hacer actualizaciones mediante SQL. Para determinar si el controlador admite **:: SQLSetPos**, llame a **:: SQLGetInfo** con el **SQL_POS_OPERATIONS** parámetro.  
  
 Actualizaciones por posición utilizan la sintaxis SQL (de forma **WHERE CURRENT OF** \<cursorname >) para identificar una fila determinada en la tabla del origen de datos. Para determinar si el controlador admite actualizaciones por posición, llame a **:: SQLGetInfo** con el **SQL_POSITIONED_STATEMENTS** parámetro.  
  
 Por lo general, conjuntos de registros dinámicos MFC (pero no sea de sólo avance de conjuntos de registros) necesitan un controlador ODBC con el cumplimiento de la API de nivel 2. Si el controlador para el origen de datos es compatible con el conjunto de API de nivel 1, todavía puede usar tanto instantáneas actualizables y de sólo lectura y conjuntos de registros solo hacia delante, pero no los dynasets. Sin embargo, un controlador de nivel 1 puede admitir conjuntos de registros dinámicos si admite obtención extendida y cursores dinámicos. Para obtener más información sobre los niveles de compatibilidad ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).  
  
> [!NOTE]
>  Si desea utilizar instantáneas y conjuntos de registros dinámicos, se debe basar en dos diferentes `CDatabase` objetos (dos conexiones distintas).  
  
 A diferencia de instantáneas, que usan almacenamiento intermedio mantenido por la biblioteca de cursores ODBC, conjuntos de registros dinámicos obtienen un registro directamente desde el origen de datos en cuanto se desplaza a él. Esto evita que los registros seleccionados originalmente por el conjunto de registros dinámicos sincronizado con el origen de datos.  
  
 Para obtener una lista de controladores ODBC incluidos en esta versión de Visual C++ y para obtener información acerca de cómo obtener controladores adicionales, consulte [lista de controladores ODBC](../../data/odbc/odbc-driver-list.md).  
  
## <a name="see-also"></a>Vea también  
 [Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)