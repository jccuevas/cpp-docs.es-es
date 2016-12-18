---
title: "C&#243;mo: Calcular las referencias de un tipo de datos VARIANT para ADO.NET (C++/CLI) | Microsoft Docs"
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
  - "ADO.NET [C++], calcular las referencias de tipos VARIANT"
  - "VARIANT"
  - "VARIANT, calcular las referencias"
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de un tipo de datos VARIANT para ADO.NET (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muestra cómo agregar un tipo de datos `VARIANT` nativo a una base de datos y cómo calcular las referencias de <xref:System.Object?displayProperty=fullName> a partir de una base de datos para un tipo de datos `VARIANT` nativo.  
  
## Ejemplo  
 En este ejemplo, la clase DatabaseClass se crea para interactuar con un objeto <xref:System.Data.DataTable> de ADO.NET.  Tenga en cuenta que esta clase es una `class` de C\+\+ nativa \(si se compara con una `ref class` o `value class`\).  Esto es necesario porque deseamos utilizar esta clase desde código nativo y no se pueden utilizar tipos administrados en código nativo.  Esta clase se compilará para CLR, según indica la directiva `#pragma managed` que precede a la declaración de clase.  Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Tenga en cuenta el miembro privado de la clase DatabaseClass: `gcroot<DataTable ^> table`.  Como los tipos nativos no pueden contener tipos administrados, es necesario utilizar la palabra clave `gcroot`.  Para obtener más información sobre `gcroot`, vea [Cómo: Declarar controladores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 El resto del código de este ejemplo es código nativo de C\+\+, según indica la directiva `#pragma unmanaged` que precede a `main`.  En este ejemplo, se crea una nueva instancia de DatabaseClass y se llama a sus métodos para crear una tabla y rellenar algunas filas de ésta.  Observe que los tipos `VARIANT` nativos se pasan como valores de la columna de base de datos ObjectCol.  Dentro de DatabaseClass, estos tipos `VARIANT` se convierten en objetos administrados utilizando la funcionalidad de cálculo de referencias que se encuentra en el espacio de nombres <xref:System.Runtime.InteropServices?displayProperty=fullName>.  En concreto, el método <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> se utiliza para calcular las referencias de `VARIANT` para <xref:System.Object> y el método <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> se utiliza para calcular las referencias de <xref:System.Object> para `VARIANT`.  
  
```  
// adonet_marshal_variant.cpp  
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
  
    void AddRow(VARIANT *objectColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(  
            IntPtr(objectColValue));  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",  
            Type::GetType("System.Object"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,  
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
            // Marshal each column value from a managed object  
            // to a VARIANT.  
            Marshal::GetNativeVariantForObject(  
                rows[i][columnStr], IntPtr(&values[i]));  
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
  
    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");  
    VARIANT v1;  
    v1.vt = VT_BSTR;  
    v1.bstrVal = bstr1;  
    db->AddRow(&v1);  
  
    int i = 42;  
    VARIANT v2;  
    v2.vt = VT_I4;  
    v2.lVal = i;  
    db->AddRow(&v2);  
  
    // Now retrieve the rows and display their contents.  
    VARIANT values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ObjectCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        switch (values[i].vt)  
        {  
            case VT_BSTR:  
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;  
                break;  
            case VT_I4:  
                cout << "ObjectCol: " << values[i].lVal << endl;  
                break;  
            default:  
                break;  
        }  
  
    }  
  
    SysFreeString(bstr1);  
    delete db;  
  
    return 0;  
}  
```  
  
  **ObjectCol: This is a BSTR in a VARIANT.**  
**ObjectCol: 42**   
## Compilar el código  
  
-   Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet\_marshal\_variant.cpp y escriba la instrucción siguiente:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## Seguridad de .NET Framework  
 Para obtener información sobre problemas de seguridad relacionados con ADO.NET, vea [Proteger aplicaciones de ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md).  
  
## Vea también  
 <xref:System.Runtime.InteropServices>   
 [Acceso a datos en ASP.NET \(Visual Studio\)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/es-es/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)