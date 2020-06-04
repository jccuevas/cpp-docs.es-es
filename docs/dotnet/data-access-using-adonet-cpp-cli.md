---
title: Acceso a datos mediante ADO.NET (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
ms.openlocfilehash: 35633449c4c01f5c103dcd54b81c0d6aa7c08cdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364410"
---
# <a name="data-access-using-adonet-ccli"></a>Acceso a datos mediante ADO.NET (C++/CLI)

ADO.NET es la API de .NET Framework para el acceso a datos y proporciona potencia y facilidad de uso sin igual por las soluciones de acceso a datos anteriores. En esta sección se describen algunos de los problemas relacionados con ADO.NET que son exclusivos de los usuarios de Visual C++, como el cálculo de referencias de tipos nativos.

ADO.NET se ejecuta en Common Language Runtime (CLR). Por lo tanto, cualquier aplicación que interactúa con ADO.NET también debe tener como destino CLR. Sin embargo, eso no significa que las aplicaciones nativas no puedan usar ADO.NET. En estos ejemplos se muestra cómo interactuar con una base de datos ADO.NET desde código nativo.

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>Cadenas del mariscal ANSI para ADO.NET

Muestra cómo agregar una cadena`char *`nativa ( ) a <xref:System.String?displayProperty=fullName> una base de datos y cómo calcular las referencias de una base de datos a una cadena nativa.

### <a name="example"></a>Ejemplo

En este ejemplo, la clase DatabaseClass se <xref:System.Data.DataTable> crea para interactuar con un objeto ADO.NET. Tenga en cuenta que esta `class` clase es un `ref class` `value class`C++ nativo (en comparación con a o ). Esto es necesario porque queremos usar esta clase desde código nativo y no se pueden usar tipos administrados en código nativo. Esta clase se compilará para tener como destino `#pragma managed` el CLR, como se indica en la directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).

Tenga en cuenta el miembro `gcroot<DataTable ^> table`privado de la clase DatabaseClass: . Dado que los tipos nativos no pueden contener tipos administrados, la `gcroot` palabra clave es necesaria. Para obtener `gcroot`más información sobre , vea [Cómo: Declarar identificadores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).

El resto del código de este ejemplo es código C++ `#pragma unmanaged` nativo, `main`como se indica en la directiva anterior . En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en cuenta que las cadenas nativas C++ se pasan como valores para la columna de base de datos StringCol. Dentro de DatabaseClass, estas cadenas se serializan en cadenas <xref:System.Runtime.InteropServices?displayProperty=fullName> administradas mediante la funcionalidad de cálculo de referencias que se encuentra en el espacio de nombres. En concreto, <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> el método se `char *` utiliza <xref:System.String>para calcular <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> las referencias <xref:System.String> de `char *`a a , y el método se utiliza para calcular las referencias a a un archivo .

> [!NOTE]
> La memoria <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> asignada por debe desasignarse llamando a una <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> o `GlobalFree`.

```cpp
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

### <a name="compiling-the-code"></a>Compilar el código

- Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_string_native.cpp y escriba la siguiente instrucción:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>Cadenas de mariscal BSTR para ADO.NET

Muestra cómo agregar una cadena`BSTR`COM ( ) a <xref:System.String?displayProperty=fullName> una base de `BSTR`datos y cómo calcular las referencias de una base de datos a un archivo .

### <a name="example"></a>Ejemplo

En este ejemplo, la clase DatabaseClass se <xref:System.Data.DataTable> crea para interactuar con un objeto ADO.NET. Tenga en cuenta que esta `class` clase es un `ref class` `value class`C++ nativo (en comparación con a o ). Esto es necesario porque queremos usar esta clase desde código nativo y no se pueden usar tipos administrados en código nativo. Esta clase se compilará para tener como destino `#pragma managed` el CLR, como se indica en la directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).

Tenga en cuenta el miembro `gcroot<DataTable ^> table`privado de la clase DatabaseClass: . Dado que los tipos nativos no pueden contener tipos administrados, la `gcroot` palabra clave es necesaria. Para obtener `gcroot`más información sobre , vea [Cómo: Declarar identificadores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).

El resto del código de este ejemplo es código C++ `#pragma unmanaged` nativo, `main`como se indica en la directiva anterior . En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en cuenta que las cadenas COM se pasan como valores para la columna de base de datos StringCol. Dentro de DatabaseClass, estas cadenas se serializan en cadenas <xref:System.Runtime.InteropServices?displayProperty=fullName> administradas mediante la funcionalidad de cálculo de referencias que se encuentra en el espacio de nombres. En concreto, <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> el método se `BSTR` utiliza <xref:System.String>para calcular <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> las referencias <xref:System.String> de `BSTR`a a , y el método se utiliza para calcular las referencias a a un archivo .

> [!NOTE]
> La memoria <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> asignada por debe desasignarse llamando a una <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> o `SysFreeString`.

``` cpp
// adonet_marshal_string_bstr.cpp
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

    void AddRow(BSTR stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringBSTR(
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

    int GetValuesForColumn(BSTR dataColumn, BSTR *values,
        int valuesLength)
    {
        // Marshal the name of the column to a managed
        // String.
        String ^columnStr = Marshal::PtrToStringBSTR(
                (IntPtr)dataColumn);

        // Get all rows in the table.
        array<DataRow ^> ^rows = table->Select();
        int len = rows->Length;
        len = (len > valuesLength) ? valuesLength : len;
        for (int i = 0; i < len; i++)
        {
            // Marshal each column value from a managed string
            // to a BSTR.
            values[i] = (BSTR)Marshal::StringToBSTR(
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

    BSTR str1 = SysAllocString(L"This is string 1.");
    db->AddRow(str1);

    BSTR str2 = SysAllocString(L"This is string 2.");
    db->AddRow(str2);

    // Now retrieve the rows and display their contents.
    BSTR values[MAXCOLS];
    BSTR str3 = SysAllocString(L"StringCol");
    int len = db->GetValuesForColumn(
        str3, values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToBSTR.
        SysFreeString(values[i]);
    }

    SysFreeString(str1);
    SysFreeString(str2);
    SysFreeString(str3);
    delete db;

    return 0;
}
```

```Output
StringCol: This is string 1.
StringCol: This is string 2.
```

### <a name="compiling-the-code"></a>Compilar el código

- Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_string_native.cpp y escriba la siguiente instrucción:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>Calcular cadenas Unicode para ADO.NET

Muestra cómo agregar una cadena`wchar_t *`Unicode nativa ( ) a <xref:System.String?displayProperty=fullName> una base de datos y cómo calcular las referencias de una base de datos a una cadena Unicode nativa.

### <a name="example"></a>Ejemplo

En este ejemplo, la clase DatabaseClass se <xref:System.Data.DataTable> crea para interactuar con un objeto ADO.NET. Tenga en cuenta que esta `class` clase es un `ref class` `value class`C++ nativo (en comparación con a o ). Esto es necesario porque queremos usar esta clase desde código nativo y no se pueden usar tipos administrados en código nativo. Esta clase se compilará para tener como destino `#pragma managed` el CLR, como se indica en la directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).

Tenga en cuenta el miembro `gcroot<DataTable ^> table`privado de la clase DatabaseClass: . Dado que los tipos nativos no pueden contener tipos administrados, la `gcroot` palabra clave es necesaria. Para obtener `gcroot`más información sobre , vea [Cómo: Declarar identificadores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).

El resto del código de este ejemplo es código C++ `#pragma unmanaged` nativo, `main`como se indica en la directiva anterior . En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en cuenta que las cadenas Unicode C++ se pasan como valores para la columna de base de datos StringCol. Dentro de DatabaseClass, estas cadenas se serializan en cadenas <xref:System.Runtime.InteropServices?displayProperty=fullName> administradas mediante la funcionalidad de cálculo de referencias que se encuentra en el espacio de nombres. En concreto, <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> el método se `wchar_t *` utiliza <xref:System.String>para calcular <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> las referencias <xref:System.String> de `wchar_t *`a a , y el método se utiliza para calcular las referencias a a un archivo .

> [!NOTE]
> La memoria <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> asignada por debe desasignarse llamando a una <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> o `GlobalFree`.

```cpp
// adonet_marshal_string_wide.cpp
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

    void AddRow(wchar_t *stringColValue)
    {
        // Add a row to the table.
        DataRow ^row = table->NewRow();
        row["StringCol"] = Marshal::PtrToStringUni(
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

    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,
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
            // Marshal each column value from a managed string
            // to a wchar_t *.
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(
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
    db->AddRow(L"This is string 1.");
    db->AddRow(L"This is string 2.");

    // Now retrieve the rows and display their contents.
    wchar_t *values[MAXCOLS];
    int len = db->GetValuesForColumn(
        L"StringCol", values, MAXCOLS);
    for (int i = 0; i < len; i++)
    {
        wcout << "StringCol: " << values[i] << endl;

        // Deallocate the memory allocated using
        // Marshal::StringToHGlobalUni.
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

### <a name="compiling-the-code"></a>Compilar el código

- Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_string_wide.cpp y escriba la siguiente instrucción:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>Marshal a VARIANT para ADO.NET

Muestra cómo agregar un `VARIANT` nativo a una base <xref:System.Object?displayProperty=fullName> de datos y `VARIANT`cómo calcular las referencias de una base de datos a una base de datos nativa.

### <a name="example"></a>Ejemplo

En este ejemplo, la clase DatabaseClass se <xref:System.Data.DataTable> crea para interactuar con un objeto ADO.NET. Tenga en cuenta que esta `class` clase es un `ref class` `value class`C++ nativo (en comparación con a o ). Esto es necesario porque queremos usar esta clase desde código nativo y no se pueden usar tipos administrados en código nativo. Esta clase se compilará para tener como destino `#pragma managed` el CLR, como se indica en la directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).

Tenga en cuenta el miembro `gcroot<DataTable ^> table`privado de la clase DatabaseClass: . Dado que los tipos nativos no pueden contener tipos administrados, la `gcroot` palabra clave es necesaria. Para obtener `gcroot`más información sobre , vea [Cómo: Declarar identificadores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).

El resto del código de este ejemplo es código C++ `#pragma unmanaged` nativo, `main`como se indica en la directiva anterior . En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en `VARIANT` cuenta que los tipos nativos se pasan como valores para la columna de base de datos ObjectCol. Dentro de DatabaseClass, estos `VARIANT` tipos se serializan en objetos <xref:System.Runtime.InteropServices?displayProperty=fullName> administrados mediante la funcionalidad de cálculo de referencias que se encuentra en el espacio de nombres. En concreto, <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> el método se `VARIANT` utiliza <xref:System.Object>para calcular <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> las referencias <xref:System.Object> de `VARIANT`a a un , y el método se utiliza para calcular las referencias de un archivo .

```cpp
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

### <a name="compiling-the-code"></a>Compilar el código

- Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_variant.cpp y escriba la siguiente instrucción:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>Mariscal a SAFEARRAY para ADO.NET

Muestra cómo agregar un `SAFEARRAY` nativo a una base de datos y cómo `SAFEARRAY`calcular las referencias de una matriz administrada de una base de datos a una base de datos nativa.

### <a name="example"></a>Ejemplo

En este ejemplo, la clase DatabaseClass se <xref:System.Data.DataTable> crea para interactuar con un objeto ADO.NET. Tenga en cuenta que esta `class` clase es un `ref class` `value class`C++ nativo (en comparación con a o ). Esto es necesario porque queremos usar esta clase desde código nativo y no se pueden usar tipos administrados en código nativo. Esta clase se compilará para tener como destino `#pragma managed` el CLR, como se indica en la directiva que precede a la declaración de clase. Para obtener más información sobre esta directiva, vea [managed, unmanaged](../preprocessor/managed-unmanaged.md).

Tenga en cuenta el miembro `gcroot<DataTable ^> table`privado de la clase DatabaseClass: . Dado que los tipos nativos no pueden contener tipos administrados, la `gcroot` palabra clave es necesaria. Para obtener `gcroot`más información sobre , vea [Cómo: Declarar identificadores en tipos nativos](../dotnet/how-to-declare-handles-in-native-types.md).

El resto del código de este ejemplo es código C++ `#pragma unmanaged` nativo, `main`como se indica en la directiva anterior . En este ejemplo, estamos creando una nueva instancia de DatabaseClass y llamando a sus métodos para crear una tabla y rellenar algunas filas de la tabla. Tenga en `SAFEARRAY` cuenta que los tipos nativos se pasan como valores para la columna de base de datos ArrayIntsCol. Dentro de DatabaseClass, estos `SAFEARRAY` tipos se serializan en objetos <xref:System.Runtime.InteropServices?displayProperty=fullName> administrados mediante la funcionalidad de cálculo de referencias que se encuentra en el espacio de nombres. En concreto, <xref:System.Runtime.InteropServices.Marshal.Copy%2A> el método se `SAFEARRAY` utiliza para calcular las referencias <xref:System.Runtime.InteropServices.Marshal.Copy%2A> a a una matriz administrada de `SAFEARRAY`enteros y el método se utiliza para calcular las referencias de una matriz administrada de enteros en un archivo .

```cpp
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

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="compiling-the-code"></a>Compilar el código

- Para compilar el código desde la línea de comandos, guarde el ejemplo de código en un archivo denominado adonet_marshal_safearray.cpp y escriba la siguiente instrucción:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>Seguridad de .NET Framework

Para obtener información sobre los problemas de seguridad que afectan a ADO.NET, consulte [Protección](/dotnet/framework/data/adonet/securing-ado-net-applications)de aplicaciones ADO.NET .

## <a name="related-sections"></a>Secciones relacionadas

|Sección|Descripción|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Proporciona información general sobre ADO.NET, un conjunto de clases que exponen los servicios de acceso a datos al programador de .NET.|

## <a name="see-also"></a>Consulte también

[Programación de .NET con C+/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Interoperabilidad nativa y de .NET](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Interoperabilidad](/dotnet/framework/interop/index)
