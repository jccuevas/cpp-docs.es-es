---
title: 'Cómo: serializar cadenas ANSI para ADO.NET (C++ / CLI) | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
ms.assetid: 6759d5a2-515f-4079-856b-73b1c1e68f2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d06f12a8a8d900e4604bea2800a1ba4c5c966770
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137476"
---
# <a name="how-to-marshal-ansi-strings-for-adonet-ccli"></a>Cómo: serializar cadenas ANSI para ADO.NET (C++/CLI)
Muestra cómo agregar una cadena nativa (`char *`) a una base de datos y cómo calcular las referencias de un <xref:System.String?displayProperty=fullName> desde una base de datos en una cadena nativa.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, la clase DatabaseClass se crea para interactuar con un ADO.NET <xref:System.Data.DataTable> objeto. Tenga en cuenta que esta clase es C++ nativo `class` (en comparación con un `ref class` o `value class`). Esto es necesario porque deseamos utilizar esta clase desde código nativo y no puede usar los tipos administrados en código nativo. Esta clase se compilará para CLR, tal y como se indica mediante el `#pragma managed` directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, consulte [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Tenga en cuenta el miembro privado de la clase DatabaseClass: `gcroot<DataTable ^> table`. Puesto que los tipos nativos no pueden contener tipos administrados, el `gcroot` palabra clave es necesaria. Para obtener más información sobre `gcroot`, consulte [Cómo: declarar controla en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 El resto del código de este ejemplo es código C++ nativo, tal y como se indica mediante el `#pragma unmanaged` anterior a la directiva `main`. En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en cuenta que las cadenas nativas de C++ se pasan como valores para la columna de base de datos StringCol. Dentro de DatabaseClass, estas cadenas se convierten en cadenas administradas utilizando la funcionalidad de cálculo de referencias en el <xref:System.Runtime.InteropServices?displayProperty=fullName> espacio de nombres. En concreto, el método <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> se utiliza para calcular las referencias de un `char *` a una <xref:System.String>y el método <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> se utiliza para calcular las referencias de un <xref:System.String> a una `char *`.  
  
> [!NOTE]
>  La memoria asignada por <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> debe desasignarse llamando <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> o `GlobalFree`.  
  
```  
// adonet_marshal_string_native.cpp  
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
  
    void AddRow(char *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringAnsi(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(char *dataColumn, char **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringAnsi(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a char *.  
            values[i] = (char *)Marshal::StringToHGlobalAnsi(  
                (String ^)rows[i][columnStr]).ToPointer();  
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
    db->AddRow("This is string 1.");  
    db->AddRow("This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    char *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        "StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        cout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalAnsi.  
        GlobalFree(values[i]);  
    }  
  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
  
-   Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_string_native.cpp y escriba la siguiente instrucción:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Para obtener información sobre problemas de seguridad que afectan a ADO.NET, vea [proteger aplicaciones de ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices>   
 [Acceso a datos mediante ADO.NET (C++ / CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Interoperabilidad](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)