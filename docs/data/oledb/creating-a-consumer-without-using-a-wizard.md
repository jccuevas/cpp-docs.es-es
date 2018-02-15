---
title: Crear un consumidor sin utilizar un asistente | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a61de0a4621f6f9387da23093f9f450749129ac3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Crear un consumidor sin utilizar un asistente
En el siguiente ejemplo se da por supuesto que va a agregar compatibilidad con los consumidores OLE DB a un proyecto ATL existente. Si desea agregar compatibilidad con los consumidores OLE DB a una aplicación MFC, debe ejecutar al Asistente para aplicaciones MFC, que crea todo el código necesario e invoca las rutinas MFC necesarias para ejecutar la aplicación.  
  
 Para agregar compatibilidad con los consumidores OLE DB sin usar al Asistente para consumidores OLE DB ATL:  
  
-   En el archivo Stdafx.h, agregue lo siguiente `#include` instrucciones:  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 Mediante programación, un consumidor normalmente realiza la siguiente secuencia de operaciones:  
  
-   Cree una clase de registro de usuario que enlaza las columnas a las variables locales. En este ejemplo, `CMyTableNameAccessor` es la clase de registro de usuario (vea [registros de usuario](../../data/oledb/user-records.md)). Esta clase contiene el mapa de columnas y la asignación de parámetro. Declare un miembro de datos en la clase de registro de usuario para cada campo que se especifica en la asignación de columna; para cada uno de estos miembros de datos, declarar un miembro de datos de estado y un miembro de datos de longitud. Para obtener más información, consulte [miembros de datos de estado de campo en los descriptores de acceso](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
    > [!NOTE]
    >  Si escribe su propio consumidor, las variables de datos deben figurar antes que las variables de estado y longitud.  
  
-   Crear una instancia de un origen de datos y una sesión. Decidir qué tipo de descriptor de acceso y el conjunto de filas a usar y, a continuación, crear una instancia de un conjunto de filas utilizando [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>  
    ```  
  
-   Llame a **CoInitialize** para inicializar COM. Esto se suele llamar en el código principal. Por ejemplo:  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   Llame a [CDataSource:: Open](../../data/oledb/cdatasource-open.md) o uno de sus variaciones.  
  
-   Abrir una conexión al origen de datos, abra la sesión y abra e inicializar el conjunto de filas (y si un comando, ejecutarlo):  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   Si lo desea, conjunto de propiedades de rowset mediante `CDBPropSet::AddProperty` y pasarlas como parámetro a `rs.Open`. Para obtener un ejemplo de cómo hacerlo, vea GetRowsetProperties en [generadas métodos](../../data/oledb/consumer-wizard-generated-methods.md).  
  
-   Ahora puede usar el conjunto de filas para recuperar o manipular los datos.  
  
-   Cuando se realiza la aplicación, cerrar la conexión, la sesión y el conjunto de filas:  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     Si se utiliza un comando, puede llamar a `ReleaseCommand` después **cerrar**. El ejemplo de código en [CCommand:: Close](../../data/oledb/ccommand-close.md) muestra cómo llamar a **cerrar** y `ReleaseCommand`.  
  
-   Llame a **CoUnInitialize** para cancelar la inicialización de COM. Esto se suele llamar en el código principal.  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Crear un consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)