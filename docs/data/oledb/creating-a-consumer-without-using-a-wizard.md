---
title: "Crear un consumidor sin utilizar un asistente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "consumidores OLE DB, crear"
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un consumidor sin utilizar un asistente
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En el ejemplo siguiente se supone que se va a agregar compatibilidad con los consumidores OLE DB a un proyecto ATL existente.  Si se desea agregar compatibilidad con los consumidores OLE DB a una aplicación MFC, se debe ejecutar el Asistente para aplicaciones MFC, que crea todo el código necesario e invoca las rutinas MFC necesarias para ejecutar la aplicación.  
  
 Para agregar compatibilidad con consumidores OLE DB sin usar el Asistente para consumidores OLE DB ATL:  
  
-   En el archivo Stdafx.h, agregue las instrucciones `#include` siguientes:  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 Un consumidor suele realizar, mediante programación, la siguiente secuencia de operaciones:  
  
-   Crear una clase de registro de usuario que enlace las columnas con variables locales.  En este ejemplo, `CMyTableNameAccessor` es la clase de registro de usuario \(vea [Registros de usuario](../../data/oledb/user-records.md)\).  Esta clase contiene el mapa de columnas y el mapa de parámetros.  Declare un miembro de datos en la clase de registro de usuario para cada campo que especifique en el mapa de columnas; para cada uno de estos miembros de datos, declare también un miembro de datos de estado y un miembro de datos de longitud.  Para obtener más información, vea [Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
    > [!NOTE]
    >  Si se crea un consumidor personalizado, las variables de datos deben figurar antes que las variables de estado y longitud.  
  
-   Crear instancias de un origen de datos y una sesión.  Decida qué tipo de descriptor de acceso y conjunto de filas se debe utilizar y, a continuación, cree una instancia de un conjunto de filas mediante [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor> >  
    ```  
  
-   Llamar a **CoInitialize** para inicializar COM.  La llamada se suele realizar en el código principal:  Por ejemplo:  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   Llamar a [CDataSource::Open](../../data/oledb/cdatasource-open.md) o una de sus variaciones.  
  
-   Abrir una conexión con el origen de datos, abrir la sesión y abrir e inicializar el conjunto de filas \(y, si se trata de un comando, ejecutarlo\):  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   Como alternativa, establecer las propiedades del conjunto de filas utilizando `CDBPropSet::AddProperty` y pasarlas como parámetro a `rs.Open`.  Para obtener un ejemplo de cómo llevarlo a cabo, vea GetRowsetProperties en [Métodos generados por el Asistente para consumidores](../../data/oledb/consumer-wizard-generated-methods.md).  
  
-   Ahora ya puede utilizar el conjunto de filas para recuperar o manipular los datos.  
  
-   Cuando la aplicación esté lista, cerrar la conexión, la sesión y el conjunto de filas:  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     Si utiliza un comando, es posible que desee llamar a `ReleaseCommand` después de a **Close**.  En el ejemplo de código que aparece en [CCommand::Close](../../data/oledb/ccommand-close.md) se muestra cómo llamar a **Close** y a `ReleaseCommand`.  
  
-   Llamar a **CoUnInitialize** para desinicializar COM.  La llamada se suele realizar en el código principal:  
  
    ```  
    CoUninitialize();  
    ```  
  
## Vea también  
 [Crear un consumidor OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)