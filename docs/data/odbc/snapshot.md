---
title: "Instantánea | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c31e08fdda3cef526f46946e45ef956f9ad1adaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="snapshot"></a>Instantánea
Una instantánea es un conjunto de registros que refleja una vista estática de los datos tal como se encontraban en el momento en que se creó la instantánea. Al abrir la instantánea y mover a todos los registros, el conjunto de registros que contiene y sus valores no cambian hasta que se vuelve a generar la instantánea mediante una llamada a **Requery**.  
  
> [!NOTE]
>  Este tema es aplicable a las clases ODBC de MFC. Si está utilizando las clases DAO de MFC en lugar de las clases ODBC de MFC, vea [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open) para obtener una descripción de los conjuntos de registros de tipo de instantánea.  
  
 Puede crear instantáneas actualizables o de solo lectura con las clases de base de datos. A diferencia de un conjunto de registros dinámicos, instantáneas actualizables no reflejan los cambios realizados por otros usuarios de valores de registro, pero reflejan las actualizaciones y eliminaciones realizados por el programa. Los registros agregados a una instantánea no se hacen visibles a la instantánea hasta que llame a **Requery**.  
  
> [!TIP]
>  Una instantánea es un cursor estático de ODBC. Los cursores estáticos no obtienen realmente una fila de datos hasta que se desplace a ese registro. Para asegurarse de que todos los registros se recuperan inmediatamente, puede desplazarse hasta el final del conjunto de registros y, a continuación, desplácese hasta el primer registro que desea ver. Sin embargo, tenga en cuenta que al final implica una sobrecarga adicional y puede reducir el rendimiento.  
  
 Las instantáneas son más útiles cuando necesite que los datos permanezcan fijos durante las operaciones, así como cuando se genera un informe o realizar cálculos. Aun así, el origen de datos puede divergir considerablemente de la instantánea, por lo que desea volver a compilarlo de vez en cuando.  
  
 Compatibilidad con las instantáneas se basa en la biblioteca de cursores ODBC, que proporciona cursores estáticos y actualizaciones con ubicación (necesarios para la actualización) para cualquier controlador de nivel 1. La biblioteca de cursores DLL debe cargarse en memoria para esta compatibilidad. Al construir un `CDatabase` objeto y llame a su `OpenEx` función miembro, debe especificar el **CDatabase:: useCursorLib** opción de la `dwOptions` parámetro. Si se llama a la **abiertos** función de miembro, la biblioteca de cursores se carga de forma predeterminada. Si está utilizando conjuntos de registros dinámicos en lugar de instantáneas, no desea hacer que la biblioteca de cursores que se va a cargar.  
  
 Las instantáneas están disponibles sólo si la biblioteca de cursores ODBC se cargó cuando la `CDatabase` objeto se construyó o el controlador ODBC que usa es compatible con los cursores estáticos.  
  
> [!NOTE]
>  Algunos controladores ODBC, las instantáneas (cursores estáticos) podrían no ser actualizables. Compruebe la documentación del controlador para los tipos de cursor admitidos y los tipos de simultaneidad que admiten. Para garantizar las instantáneas actualizables, asegúrese de cargar la biblioteca de cursores en la memoria cuando se crea un `CDatabase` objeto. Para obtener más información, consulte [ODBC: biblioteca de cursores ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Si desea utilizar instantáneas y conjuntos de registros dinámicos, se debe basar en dos diferentes `CDatabase` objetos (dos conexiones distintas).  
  
 Para obtener más información sobre el recurso compartido de instantáneas de propiedades con todos los conjuntos de registros, vea [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md). Para obtener más información sobre ODBC y las instantáneas, incluida la biblioteca de cursores ODBC, vea [ODBC](../../data/odbc/odbc-basics.md).  
  
## <a name="see-also"></a>Vea también  
 [Conectividad abierta de bases de datos (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)