---
title: "C&#243;mo: Calcular las referencias de una matriz SAFEARRAY de ADO.NET (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO.NET [C++], calcular las referencias de tipos SAFEARRAY"
  - "SAFEARRAY, calcular las referencias"
ms.assetid: 1034b9d7-ecf1-40f7-a9ee-53180e87a58c
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de una matriz SAFEARRAY de ADO.NET (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muestra cómo agregar una matriz `SAFEARRAY` nativa a una base de datos y cómo calcular las referencias a una matriz administrada de una base de datos a una matriz `SAFEARRAY` nativa.  
  
## Ejemplo  
 En este ejemplo, la clase DatabaseClass se crea para interactuar con un objeto <xref:System.Data.DataTable> de ADO.NET.  Tenga en cuenta que esta clase es una `class` de C\+\+ nativa \(si se compara con una `ref class` o `value class`\).  Esto es necesario porque deseamos utilizar esta clase desde código nativo y no se pueden utilizar tipos administrados en código nativo.  Esta clase se compilará para CLR, según indica la directiva `#pragma managed` que precede a la declaración de clase.  Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Tenga en cuenta el miembro privado de la clase DatabaseClass: `gcroot<DataTable ^> table`.  Como los tipos nativos no pueden contener tipos administrados, es necesario utilizar la palabra clave `gcroot`.  Para obtener más información sobre `gcroot`, vea [Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 El resto del código de este ejemplo es código nativo de C\+\+, según indica la directiva `#pragma unmanaged` que precede a `main`.  En este ejemplo, se crea una nueva instancia de DatabaseClass y se llama a sus métodos para crear una tabla y rellenar algunas filas de ésta.  Observe que los tipos `SAFEARRAY` nativos se pasan como valores para la columna de base de datos ArrayIntsCol.  Dentro de DatabaseClass, estos tipos `SAFEARRAY` se convierten en objetos administrados utilizando la funcionalidad de cálculo de referencias que encontramos en el espacio de nombres <xref:System.Runtime.InteropServices?displayProperty=fullName>.  En concreto, el método <xref:System.Runtime.InteropServices.Marshal.Copy%2A> se utiliza para calcular las referencias de `SAFEARRAY` para una matriz administrada de enteros, y el método <xref:System.Runtime.InteropServices.Marshal.Copy%2A> para calcular las referencias de una matriz administrada de enteros para `SAFEARRAY`.  
  
```  
// adonet_marshal_safearray.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(SAFEARRAY *arrayIntsColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        int len = arrayIntsColValue->rgsabound[0].cElements;  
        array<int> ^arr = gcnew array<int>(len);  
  
        int *pData;  
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);  
        Marshal::Copy(IntPtr(pData), arr, 0, len);  
        SafeArrayUnaccessData(arrayIntsColValue);  
  
        row["ArrayIntsCol"] = arr;  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",  
            Type::GetType("System.Int32[]"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed array  
            // of Int32s to a SAFEARRAY of type VT_I4.  
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);  
            int *pData;  
            SafeArrayAccessData(values[i], (void **)&pData);  
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,  
                IntPtr(pData), 10);  
            SafeArrayUnaccessData(values[i]);  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
  
    // Create a standard array.  
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
    // Create a SAFEARRAY.  
    SAFEARRAY *psa;  
    psa = SafeArrayCreateVector(VT_I4, 0, 10);  
  
    // Copy the data from the original array to the SAFEARRAY.  
    int *pData;  
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);  
    memcpy(pData, &originalArray, 40);  
    SafeArrayUnaccessData(psa);  
    db->AddRow(psa);  
  
    // Now retrieve the rows and display their contents.  
    SAFEARRAY *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ArrayIntsCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        int *pData;  
        SafeArrayAccessData(values[i], (void **)&pData);  
        for (int j = 0; j < 10; j++)  
        {  
            cout << pData[j] << " ";  
        }  
        cout << endl;  
        SafeArrayUnaccessData(values[i]);  
  
        // Deallocate the memory allocated using  
        // SafeArrayCreateVector.  
        SafeArrayDestroy(values[i]);  
    }  
  
    SafeArrayDestroy(psa);  
    delete db;  
  
    return 0;  
}  
```  
  
  **0 1 2 3 4 5 6 7 8 9**    
## Compilar el código  
  
-   Para compilar el código de la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet\_marshal\_safearray.cpp y escriba la instrucción siguiente:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## Seguridad de .NET Framework  
 Para obtener información sobre problemas de seguridad relacionados con ADO.NET, vea [Proteger aplicaciones de ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md).  
  
## Vea también  
 <xref:System.Runtime.InteropServices>   
 [Acceso a datos en ASP.NET \(Visual Studio\)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/es-es/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)