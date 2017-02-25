---
title: "Obtener datos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos [C++], obtener"
  - "obtener"
  - "plantillas de consumidor OLE DB [C++], obtener datos"
  - "conjuntos de filas [C++], obtener"
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Obtener datos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al abrir los objetos de origen de datos, sesión y conjuntos de filas es posible obtener o recuperar datos.  Según el tipo de descriptor de acceso que estemos utilizando, puede resultar conveniente enlazar las columnas.  
  
### Para obtener datos  
  
1.  Abra el conjunto de filas con el comando **Open** correspondiente.  
  
2.  Si utiliza `CManualAccessor`, enlace las columnas de resultados si aún no lo ha hecho.  Para enlazar las columnas, llame a `GetColumnInfo` y después cree un descriptor de acceso con los enlaces, como se muestra en el siguiente ejemplo:  
  
    ```  
    // From the DBViewer Sample CDBTreeView::OnQueryEdit  
    // Get the column information  
    ULONG ulColumns       = 0;  
    DBCOLUMNINFO* pColumnInfo  = NULL;  
    LPOLESTR pStrings      = NULL;  
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)  
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);  
    struct MYBIND* pBind = new MYBIND[ulColumns];  
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);  
    for (ULONG l=0; l<ulColumns; l++)  
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);  
    rs.Bind();  
    ```  
  
3.  Cree un bucle `while` para recuperar los datos.  En el bucle, llame a `MoveNext` para hacer avanzar el cursor y probar el valor devuelto con S\_OK, como se muestra en el siguiente ejemplo:  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  Dentro del bucle `while`, se pueden recuperar los datos de acuerdo con el tipo de descriptor de acceso.  
  
    -   Si utiliza la clase [CAccessor](../../data/oledb/caccessor-class.md), debe haber un registro de usuario que contenga los miembros de datos.  Se puede obtener acceso a los datos por medio de esos miembros de datos, como se muestra en el siguiente ejemplo:  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   Si utiliza la clase `CDynamicAccessor` o `CDynamicParameterAccessor`, puede recuperar datos mediante las funciones de acceso `GetValue` y `GetColumn`, como se muestra en el ejemplo siguiente.  Si desea determinar el tipo de datos que está utilizando, use `GetType`.  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the dynamic accessor functions to retrieve your data.  
  
            ULONG ulColumns = rs.GetColumnCount();  
            for (ULONG i=0; i<ulColumns; i++)  
            {  
                rs.GetValue(i);  
            }  
        }  
        ```  
  
    -   Si utiliza `CManualAccessor`, debe especificar sus propios miembros de datos, enlazarlos personalmente y obtener acceso a ellos directamente, como se muestra en el ejemplo siguiente:  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## Vea también  
 [Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)