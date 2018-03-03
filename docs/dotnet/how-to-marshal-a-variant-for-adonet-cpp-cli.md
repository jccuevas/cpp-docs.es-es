---
title: "Cómo: calcular las referencias de una variante para ADO.NET (C++ / CLI) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 504f9553b85acefa085a7a8d6c85768ff934bab7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-a-variant-for-adonet-ccli"></a>Cómo: serializar un tipo de datos VARIANT para ADO.NET (C++/CLI)
Muestra cómo agregar nativo `VARIANT` a una base de datos y cómo calcular las referencias de un <xref:System.Object?displayProperty=fullName> desde una base de datos nativo `VARIANT`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la clase DatabaseClass se crea para interactuar con un ADO.NET <xref:System.Data.DataTable> objeto. Tenga en cuenta que esta clase es C++ nativo `class` (en comparación con un `ref class` o `value class`). Esto es necesario porque deseamos utilizar esta clase desde código nativo y no puede usar los tipos administrados en código nativo. Esta clase se compilará para CLR, tal y como se indica mediante el `#pragma managed` directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, consulte [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Tenga en cuenta el miembro privado de la clase DatabaseClass: `gcroot<DataTable ^> table`. Puesto que los tipos nativos no pueden contener tipos administrados, el `gcroot` palabra clave es necesaria. Para obtener más información sobre `gcroot`, consulte [Cómo: declarar controla en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 El resto del código de este ejemplo es código C++ nativo, tal y como se indica mediante el `#pragma unmanaged` anterior a la directiva `main`. En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en cuenta que nativo `VARIANT` tipos nativos se pasan como valores para la columna de base de datos ObjectCol. Dentro de DatabaseClass, estos `VARIANT` tipos se convierten en objetos administrados utilizando la funcionalidad de cálculo de referencias en el <xref:System.Runtime.InteropServices?displayProperty=fullName> espacio de nombres. En concreto, el método <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> se utiliza para calcular las referencias de un `VARIANT` a una <xref:System.Object>y el método <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> se utiliza para calcular las referencias de un <xref:System.Object> a una `VARIANT`.  
  
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
  
```Output  
ObjectCol: This is a BSTR in a VARIANT.  
ObjectCol: 42  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
  
-   Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_variant.cpp y escriba la siguiente instrucción:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Para obtener información sobre problemas de seguridad que afectan a ADO.NET, vea [proteger aplicaciones de ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices>   
 [Acceso a datos mediante ADO.NET (C++ / CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Interoperabilidad](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)