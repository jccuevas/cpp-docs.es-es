---
title: "Exploración del sistema de archivos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7ed9a10434f0128de871a426f7e6be46212d4098
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="file-system-navigation"></a>Exploración del sistema de archivos
El encabezado \<filesystem> implementa la especificación técnica del sistema de archivos de C++ ISO/IEC TS 18822:2015 (borrador final: [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)) y tiene tipos y funciones que le permiten escribir código independiente de la plataforma para navegar por el sistema de archivos. Al ser multiplataforma, contiene algunas API que no son relevantes para los sistemas Windows. Por ejemplo, esto significa que `is_fifo(const path&)` siempre devuelve `false` en Windows.   
  
## <a name="overview"></a>Información general  
Use las API \<filesystem> para las siguientes tareas:  
  
-   Iterar en los archivos y directorios que se encuentren bajo una ruta de acceso especificada.  
  
-   Obtener información acerca de los archivos, incluidos la hora de creación, el tamaño, la extensión y el directorio raíz.  
  
-   Componer, descomponer y comparar rutas de acceso.  
  
-   Crear, copiar y eliminar directorios.  
  
-   Copiar y eliminar archivos.  
  
Para obtener más información sobre la E/S de archivo que usa la biblioteca estándar, vea [Programación con iostream](../standard-library/iostream-programming.md).  
  
## <a name="paths"></a>Rutas de acceso  
  
### <a name="constructing-and-composing-paths"></a>Crear y componer rutas de acceso  
Desde Windows XP las rutas de acceso de Windows se almacenan de forma nativa en Unicode. La clase [path](../standard-library/path-class.md) realiza de forma automática todas las conversiones de cadena necesarias. Acepta argumentos de matrices de caracteres anchos y estrechos, así como los tipos `std::string` y `std::wstring` con formato UTF8 o UTF16. La clase `path` también normaliza automáticamente los separadores de ruta de acceso. Puede utilizar una sola barra diagonal como separador de directorios en los argumentos del constructor. Esto le permite utilizar las mismas cadenas para almacenar rutas de acceso tanto en entornos Windows como UNIX:  
  
```cpp  
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!  
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always  
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.  
```  
  
Para concatenar dos rutas de acceso, puede usar los operadores sobrecargados `/` y `/=` , que son análogos a los operadores `+` y `+=` en `std::string` y `std::wstring`. El objeto `path` facilitará de forma oportuna los separadores si usted no lo hace.  
  
```cpp  
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!  
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot  
```  
  
### <a name="examining-paths"></a>Examinar rutas de acceso  
La clase path tiene varios métodos que devuelven información acerca de diversas partes de la propia ruta, a diferencia de la entidad del sistema de archivos a la que podría hacer referencia. Puede obtener, entre otros, la raíz, la ruta de acceso relativa, el nombre de archivo o la extensión de archivo. Puede iterar sobre un objeto de ruta de acceso para examinar todas las carpetas de la jerarquía. En el siguiente ejemplo se muestra cómo realizar una iteración en una ruta de acceso (no en el directorio al que hace referencia) y recuperar información acerca de sus partes.  
  
```cpp  
// filesystem_path_example.cpp  
// compile by using: /EHsc  
#include <string>  
#include <iostream>  
#include <sstream>  
#include <filesystem>  
  
using namespace std;  
using namespace std::experimental::filesystem;  
  
wstring DisplayPathInfo()  
{  
    // This path may or may not refer to an existing file. We are   
    // examining this path string, not file system objects.  
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");  
  
    wostringstream wos;  
    int i = 0;  
    wos << L"Displaying path info for: " << pathToDisplay << endl;  
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)  
    {  
        wos << L"path part: " << i++ << L" = " << *itr << endl;  
    }  
  
    wos << L"root_name() = " << pathToDisplay.root_name() << endl  
        << L"root_path() = " << pathToDisplay.root_path() << endl  
        << L"relative_path() = " << pathToDisplay.relative_path() << endl  
        << L"parent_path() = " << pathToDisplay.parent_path() << endl  
        << L"filename() = " << pathToDisplay.filename() << endl  
        << L"stem() = " << pathToDisplay.stem() << endl  
        << L"extension() = " << pathToDisplay.extension() << endl;  
  
    return wos.str();  
}  
  
void main(int argc, char* argv[])  
{  
    wcout << DisplayPathInfo() << endl;  
    // wcout << ComparePaths() << endl; // see following example  
    wcout << endl << L"Press Enter to exit" << endl;  
    wstring input;  
    getline(wcin, input);  
}  
```  
  
El ejemplo produce esta salida:  
  
```Output  
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt  
path part: 0 = C:  
path part: 1 = \  
path part: 2 = FileSystemTest  
path part: 3 = SubDir3  
path part: 4 = SubDirLevel2  
path part: 5 = File2.txt  
root_name() = C:  
root_path() = C:\  
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt  
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2  
filename() = File2.txt  
stem() = File2  
extension() = .txt  
```  
  
### <a name="comparing-paths"></a>Comparar rutas de acceso  
La clase `path` sobrecarga los mismos operadores de comparación que `std::string` y `std::wstring`. Cuando se comparan dos rutas de acceso, se realiza una comparación de cadenas una vez que se han normalizado los separadores. Si falta una barra diagonal final (o barra diagonal inversa), no se agrega y afecta a la comparación. En el siguiente ejemplo se muestra cómo se comparan los valores de ruta de acceso:  
  
```cpp  
wstring ComparePaths()  
{  
    path p0(L"C:/Documents");                 // no trailing separator  
    path p1(L"C:/Documents/");                // p0 < p1  
    path p2(L"C:/Documents/2013/");           // p1 < p2      
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3  
    path p4(L"C:/Documents/2014/");           // p3 < p4   
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5  

    wostringstream wos;  
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;  
    return wos.str();
}  
```  
  
```Output  
C:\Documents < C:\Documents\: true  
C:\Documents\ < C:\Documents\2013\: true  
C:\Documents\2013\ < C:\Documents\2013\Reports\: true  
C:\Documents\2013\Reports\ < C:\Documents\2014\: true  
C:\Documents\2014\ < D:\Documents\2013\Reports\: true  
```  
  
Para ejecutar este código, péguelo en el ejemplo anterior completo antes de `main` y quite la marca de comentario de la línea que lo llama en main.  
  
### <a name="converting-between-path-and-string-types"></a>Convertir entre tipos de ruta de acceso y de cadena  
Un objeto `path` se puede convertir implícitamente a `std::wstring` o `std::string`. Esto significa que puede pasar una ruta de acceso a funciones como [wofstream::open](../standard-library/basic-ofstream-class.md#open), tal como se muestra en este ejemplo:  
  
```cpp  
// filesystem_path_conversion.cpp  
// compile by using: /EHsc  
#include <string>  
#include <iostream>  
#include <fstream>  
#include <filesystem>  

using namespace std;
using namespace std::experimental::filesystem;

void main(int argc, char* argv[])
{
    wchar_t* p = L"C:/Users/Public/Documents";
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.  
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```  
  
```Output  
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit  
```  
  
## <a name="iterating-directories-and-files"></a>Iterar directorios y archivos  
El encabezado \<filesystem> proporciona el tipo [directory_iterator](../standard-library/directory-iterator-class.md) para iterar en directorios individuales y la clase [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) para iterar de manera recursiva en un directorio y sus subdirectorios. Después de crear un iterador pasándole un objeto `path` , el iterador apunta al primer elemento directory_entry de la ruta de acceso. Cree el iterador de fin llamando al constructor predeterminado.  
  
Cuando se itera en un directorio, se puede encontrar con varios tipos de elementos, incluyendo directorios, archivos, vínculos simbólicos y archivos de socket. El `directory_iterator` devuelve sus elementos como objetos [directory_entry](../standard-library/directory-entry-class.md).  
