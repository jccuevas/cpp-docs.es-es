---
title: "Cómo: interfaz entre código excepcional y no excepcional | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59838fa1797fc87561b081d40143693dea385668
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>Cómo: Interfaz entre código excepcional y no excepcional
En este artículo se describe cómo implementar el control de excepciones coherente en un módulo de C++ y cómo traducir esas excepciones a códigos de error, y vicecersa, en los límites de la excepción.  
  
 A veces, un módulo de C++ tiene que servir de interfaz con código que no usa las excepciones (código sin excepciones). Dicha interfaz se conoce como un *límite de la excepción*. Por ejemplo, quizás desee llamar a la función `CreateFile` de Win32 en el programa de C++. `CreateFile` no produce excepciones; en su lugar establece los códigos de error que pueden recuperarse mediante la función `GetLastError`. Si el programa de C++ no es trivial, probablemente sea preferible tener una directiva coherente de control de errores basada en excepciones. Y probablemente no es conveniente abandonar las excepciones solo porque se interactúa con código sin excepciones; tampoco es conveniente mezclar directivas de error basadas en excepciones y no basadas en excepciones en el módulo de C++.  
  
## <a name="calling-non-exceptional-functions-from-c"></a>Llamar a funciones sin excepciones desde C++  
 Cuando se llama a una función sin excepciones desde C++, la idea es ajustar esa función en una función de C++ que detecte cualquier error y posiblemente inicie una excepción. Cuando diseñe una función contenedora, decida primero qué tipo de garantías de excepción va a proporcionar: ningún throw, segura o básica. En segundo lugar, diseñe la función para liberar correctamente todos los recursos, por ejemplo, los identificadores de archivo, si se produce una excepción. Normalmente, esto significa que utiliza punteros inteligentes o administradores de recursos similares para poseer los recursos. Para obtener más información acerca de las consideraciones de diseño, vea [Cómo: diseño de seguridad de las excepciones](../cpp/how-to-design-for-exception-safety.md).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra que las funciones de C++ que usan internamente las funciones `CreateFile` y `ReadFile` de Win32 para abrir y leer dos archivos.  La clase `File` es un contenedor RAII (Resource Acquisition Is Initialization) para los identificadores de archivo. El constructor detecta una condición de "archivo no encontrado" y produce una excepción para propagar el error en la pila de llamadas del módulo de C++ (en este ejemplo, la función `main()`). Si se produce una excepción después de que un objeto `File` se haya construido totalmente, el destructor llama automáticamente a `CloseHandle` para liberar el identificador de archivo. (Si lo prefiere, puede utilizar la clase de Active Template Library (ATL) `CHandle` para este mismo propósito o `unique_ptr` junto con un eliminador personalizado). Las funciones que llaman a las API de Win32 y CRT detectan errores y, a continuación, producen excepciones de C++ mediante la función `ThrowLastErrorIf` definida localmente, que a su vez utiliza la clase `Win32Exception`, derivada de la clase `runtime_error`. Todas las funciones de este ejemplo proporcionan una garantía de excepción segura; si se produce una excepción en cualquier momento en estas funciones, no se pierden recursos y no se modifica el estado del programa.  
  
```cpp  
// compile with: /EHsc  
#include <Windows.h>  
#include <stdlib.h>  
#include <vector>  
#include <iostream>  
#include <string>  
#include <limits>  
#include <stdexcept>  
  
using namespace std;  
  
string FormatErrorMessage(DWORD error, const string& msg)  
{  
    static const int BUFFERLENGTH = 1024;  
    vector<char> buf(BUFFERLENGTH);  
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),   
        BUFFERLENGTH - 1, 0);   
    return string(buf.data()) + "   ("  + msg  + ")";  
}  
  
class Win32Exception : public runtime_error  
{      
private:  
    DWORD m_error;  
public:  
    Win32Exception(DWORD error, const string& msg)  
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }  
  
    DWORD GetErrorCode() const { return m_error; }  
};  
  
void ThrowLastErrorIf(bool expression, const string& msg)   
{   
    if (expression) {   
        throw Win32Exception(GetLastError(), msg);   
    }   
}   
  
class File  
{  
private:  
    HANDLE m_handle;  
  
    // Declared but not defined, to avoid double closing.  
    File& operator=(const File&);  
    File(const File&);  
public:  
    explicit File(const string& filename)   
    {  
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,   
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);  
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,   
            "CreateFile call failed on file named " + filename);  
    }  
  
    ~File() { CloseHandle(m_handle); }  
  
    HANDLE GetHandle() { return m_handle; }  
};  
  
size_t GetFileSizeSafe(const string& filename)  
{  
    File fobj(filename);  
    LARGE_INTEGER filesize;  
  
    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);  
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);  
  
    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {  
        return filesize.QuadPart;  
    } else {  
        throw;   
    }  
}  
  
vector<char> ReadFileVector(const string& filename)  
{  
    File fobj(filename);  
    size_t filesize = GetFileSizeSafe(filename);  
    DWORD bytesRead = 0;  
  
    vector<char> readbuffer(filesize);  
  
    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),   
        &bytesRead, nullptr);  
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);  
  
    cout << filename << " file size: " << filesize << ", bytesRead: "   
        << bytesRead << endl;  
  
    return readbuffer;  
}  
  
bool IsFileDiff(const string& filename1, const string& filename2)   
{  
    return ReadFileVector(filename1) != ReadFileVector(filename2);  
}   
  
#include <iomanip>  
  
int main ( int argc, char* argv[] )  
{  
    string filename1("file1.txt");  
    string filename2("file2.txt");  
  
    try  
    {  
        if(argc > 2) {  
            filename1 = argv[1];  
            filename2 = argv[2];  
        }   
  
        cout << "Using file names " << filename1 << " and " << filename2 << endl;  
  
        if (IsFileDiff(filename1, filename2)) {  
            cout << "*** Files are different." << endl;  
        } else {  
            cout<< "*** Files match." << endl;  
        }  
    }  
    catch(const Win32Exception& e)  
    {          
        ios state(nullptr);  
        state.copyfmt(cout);  
        cout << e.what() << endl;  
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')   
            << e.GetErrorCode() << endl;  
        cout.copyfmt(state); // restore previous formatting  
    }  
}  
  
```  
  
## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Llamar a código con excepciones desde código sin excepciones  
 Los programas de C pueden llamar a las funciones de C++ que se declaran como "extern C". El código escrito en diferentes lenguajes puede utilizar servidores COM de C++. Al implementar funciones públicas preparadas para excepciones en C++ para que las invoque código sin excepciones, la función de C++ no debe permitir que ninguna excepción se propague de nuevo al llamador. Por consiguiente, la función de C++ debe detectar específicamente cada excepción que pueda administrar y, si es necesario, debe convertir la excepción a un código de error que el llamador comprenda. Si no se conocen todas las excepciones posibles, la función de C++ debe tener un bloque `catch(...)` como último controlador. En ese caso, es mejor notificar un error irrecuperable al llamador, porque el programa podría estar en un estado desconocido.  
  
 El ejemplo siguiente muestra una función para la que se supone que cualquier excepción que pueda producirse es Win32Exception o un tipo de excepción derivado de `std::exception`. La función detecta cualquier excepción de estos tipos y propaga la información de error como código de error Win32 al llamador.  
  
```cpp  
BOOL DiffFiles2(const string& file1, const string& file2)   
{   
    try   
    {   
        File f1(file1);   
        File f2(file2);   
        if (IsTextFileDiff(f1, f2))   
        {   
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);   
            return FALSE;   
        }   
        return TRUE;   
    }   
    catch(Win32Exception& e)   
    {   
        SetLastError(e.GetErrorCode());   
    }  
  
    catch(std::exception& e)   
    {   
        SetLastError(MY_APPLICATION_GENERAL_ERROR);   
    }   
    return FALSE;   
}  
  
```  
  
 Cuando se convierte de excepciones a códigos de error, un problema potencial se debe a que los códigos de error no contienen a menudo la riqueza de información que una excepción puede almacenar. Para resolver esto, puede proporcionar un bloque `catch` para cada tipo de excepción concreto que pueda producirse. Además, realice un registro para grabar los detalles de la excepción antes de que se convierta en un código de error. Este enfoque puede crear muchas repeticiones en el código si varias funciones usan el mismo conjunto de bloques `catch`. Una manera eficaz de evitar la repetición del código es la refactorización de los bloques en una función de utilidad privada que implemente los bloques `try` y `catch`, y que acepte un objeto de función que se invoca en el bloque `try`. En cada función pública, pase el código a la función de utilidad como una expresión lambda.  
  
```cpp  
template<typename Func>   
bool Win32ExceptionBoundary(Func&& f)   
{   
    try   
    {   
        return f();   
    }   
    catch(Win32Exception& e)   
    {   
        SetLastError(e.GetErrorCode());   
    }   
    catch(const std::exception& e)   
    {   
        SetLastError(MY_APPLICATION_GENERAL_ERROR);   
    }   
    return false;   
}  
  
```  
  
 En el ejemplo siguiente se muestra cómo escribir la expresión lambda que define el objeto de función (functor). Cuando usa una expresión lambda para definir un functor "alineado", este suele ser más fácil de leer de lo que sería si se escribe como un objeto de función con nombre.  
  
```cpp  
bool DiffFiles3(const string& file1, const string& file2)   
{   
    return Win32ExceptionBoundary([&]() -> bool  
    {   
        File f1(file1);   
        File f2(file2);   
        if (IsTextFileDiff(f1, f2))   
        {   
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);   
            return false;   
        }   
        return true;   
    });   
}  
  
```  
  
 Para obtener más información sobre las expresiones lambda, vea [Expresiones lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Controlar errores y excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Cómo: Diseñar para la seguridad de las excepciones](../cpp/how-to-design-for-exception-safety.md)