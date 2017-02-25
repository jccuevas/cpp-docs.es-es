---
title: "Exploraci&#243;n del sistema de archivos | Microsoft Docs"
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
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Exploraci&#243;n del sistema de archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El encabezado \<filesystem\> implementa el borrador de la especificación técnica del sistema de archivos \([ISO\/IEC JTC 1\/SC 22\/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)\) y tiene tipos y funciones que le permiten escribir código independiente de la plataforma para navegar por el sistema de archivos. Al ser multiplataforma, contiene algunas API que no son relevantes para los sistemas Windows. Por ejemplo, esto significa que `is_fifo(const path&)` siempre devuelve `false` en Windows. El encabezado se basa en un borrador de especificaciones técnicas que no se ha votado para incluirse en el estándar C\+\+17 antes de la publicación de Visual Studio 2015 RTM. Sus miembros se encuentran en el espacio de nombres `std::experimental::filesystem::v1`.  
  
## Información general  
 Use las API \<filesystem\> para las siguientes tareas:  
  
-   Iterar en los archivos y directorios que se encuentren bajo una ruta de acceso especificada.  
  
-   Obtener información acerca de los archivos, incluidos la hora de creación, el tamaño, la extensión y el directorio raíz.  
  
-   Componer, descomponer y comparar rutas de acceso.  
  
-   Crear, copiar y eliminar directorios.  
  
-   Copiar y eliminar archivos.  
  
 Para obtener más información sobre el E\/S de archivo que utilice la biblioteca estándar, consulte [Programación con iostream](../standard-library/iostream-programming.md).  
  
## Rutas de acceso  
  
### Crear y componer rutas de acceso  
 Desde Windows XP las rutas de acceso de Windows se almacenan de forma nativa en Unicode. La clase [path](../standard-library/path-class-cpp-standard-template-library.md) realiza automáticamente todas las conversiones de cadena necesarias. Acepta argumentos de matrices de caracteres anchos y estrechos, así como los tipos `std::string` y `std::wstring` con formato UTF8 o UTF16. La clase `path` también normaliza automáticamente los separadores de ruta de acceso. Puede utilizar una sola barra diagonal como separador de directorios en los argumentos del constructor. Esto le permite utilizar las mismas cadenas para almacenar rutas de acceso tanto en entornos Windows como UNIX:  
  
```cpp  
path pathToDisplay(L"/FileSystemTest/SubDir3"); // OK! path pathToDisplay2(L"\\FileSystemTest\\SubDir3"); // Still OK as always path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.  
```  
  
 Para concatenar dos rutas de acceso, puede usar los operadores sobrecargados  `/` y `/=`, que son análogos a los operadores `+` y `+=` en `std::string` y `std::wstring`. El objeto `path` facilitará de forma oportuna los separadores si usted no lo hace.  
  
```cpp  
path myRoot("C:/FileSystemTest"); // no trailing separator, no problem! myRoot /= path("SubDirRoot"); // C:/FileSystemTest/SubDirRoot  
```  
  
### Examinar rutas de acceso  
 La clase path tiene varios métodos que devuelven información acerca de diversas partes de la propia ruta, a diferencia de la entidad del sistema de archivos a la que podría hacer referencia. Puede obtener, entre otros, la raíz, la ruta de acceso relativa, el nombre de archivo o la extensión de archivo. Puede iterar sobre un objeto de ruta de acceso para examinar todas las carpetas de la jerarquía. En el siguiente ejemplo se muestra cómo realizar una iteración en una ruta de acceso \(no en el directorio al que hace referencia\) y recuperar información acerca de sus partes.  
  
```cpp  
  
#include <string> #include <iostream> #include <sstream> #include <filesystem> using namespace std; using namespace std::experimental::filesystem::v1; wstring  DisplayPathInfo() { // This path may or may not refer to an existing file. We are // examining this path string, not file system objects. path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt "); wostringstream wos; int i = 0; wos << L"Displaying path info for: " << pathToDisplay << endl; for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr) { wos << L"path part: " << i++ << L" = " << *itr << endl; } wos << L"root_name() = " << pathToDisplay.root_name() << endl << L"root_path() = " << pathToDisplay.root_path() << endl << L"relative_path() = " << pathToDisplay.relative_path() << endl << L"parent_path() = " << pathToDisplay.parent_path() << endl << L"filename() = " << pathToDisplay.filename() << endl << L"stem() = " << pathToDisplay.stem() << endl << L"extension() = " << pathToDisplay.extension() << endl; return wos.str(); } void main(int argc, char* argv[]) { wcout << DisplayPathInfo() << endl; // wcout << ComparePaths() << endl; // see following example wcout << endl << L"Press Enter to exit" << endl; wstring input; getline(wcin, input); }  
```  
  
 El ejemplo produce esta salida:  
  
```cpp  
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt path part: 0 = C: path part: 1 = \ path part: 2 = FileSystemTest path part: 3 = SubDir3 path part: 4 = SubDirLevel2 path part: 5 = File2.txt root_name() = C: root_path() = C:\ relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2 filename() = File2.txt stem() = File2 extension() = .txt  
```  
  
### Comparar rutas de acceso  
 La clase `path` sobrecarga los mismos operadores de comparación que `std::string` y `std::wstring`. Cuando se comparan dos rutas de acceso, se realiza una comparación de cadenas una vez que se han normalizado los separadores. Si falta una barra diagonal final \(o barra diagonal inversa\), no se agrega y afecta a la comparación. En el siguiente ejemplo se muestra cómo se comparan los valores de ruta de acceso:  
  
```cpp  
  
wstring ComparePaths() { path p0(L"C:/Documents"); // no trailing separator path p1(L"C:/Documents/"); //p0 < p1 path p2(L"C:/Documents/2013/"); // p1 < p2 path p3(L"C:/Documents/2013/Reports/"); // p2 < p3 path p4(L"C:/Documents/2014/");  // p3 < p4 path p5(L"D:/Documents/2013/Reports/"); // p4 < p5 wostringstream wos; wos << boolalpha << p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl << p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl << p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl << p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl << p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl; return wos.str(); } /* Output: C:\Documents < C:\Documents\: true C:\Documents\ < C:\Documents\2013\: true C:\Documents\2013\ < C:\Documents\2013\Reports\: true C:\Documents\2013\Reports\ < C:\Documents\2014\: true C:\Documents\2014\ < D:\Documents\2013\Reports\: true */  
```  
  
 Para ejecutar este código, péguelo en el ejemplo anterior completo y elimine la línea que lo llama en main.  
  
### Convertir entre tipos de ruta de acceso y de cadena  
 Un objeto `path` se puede convertir implícitamente a `std::wstring` o `std::string`. Esto significa que puede pasar una ruta de acceso a funciones como [wofstream::open](../Topic/basic_ofstream::open.md), tal como se muestra en este ejemplo:  
  
```cpp  
wchar_t* p = L"C:/test"; path filePath(p); filePath /= L"NewFile.txt"; // Open, write to, and close the file. wofstream myFile; myFile.open(filePath); myFile << L"Lorem ipsum..."; myFile.close  
  
```  
  
## Iterar directorios y archivos  
 El encabezado \<filesystem\> proporciona el tipo [directory\_iterator](../standard-library/directory-iterator-class.md) para iterar en directorios individuales y la clase [recursive\_directory\_iterator](../standard-library/recursive-directory-iterator-class.md) para iterar de manera recursiva en un directorio y sus subdirectorios. Después de crear un iterador pasándole un objeto `path`, el iterador apunta al primer elemento directory\_entry de la ruta de acceso. Cree el iterador de fin llamando al constructor predeterminado.  
  
 Cuando se itera en un directorio, se puede encontrar con varios tipos de elementos, incluyendo directorios, archivos, vínculos simbólicos y archivos de socket.`directory_iterator` devuelve sus elementos como objetos [directory\_entry](../standard-library/directory-entry-class.md) y cada objeto tiene un miembro [status\(\)](http://msdn.microsoft.com/es-es/a70a3c55-3a76-417f-abaf-862ff94b2056) que indica el tipo de entrada que está examinando. Mediante el examen de este valor, puede tomar decisiones sobre qué hacer con cualquier entrada determinada. En el siguiente ejemplo se realiza una iteración en un directorio individual y si la entrada de directorio es un archivo normal, el código imprime algo de información acerca de dicho archivo. Si la entrada es un directorio, solo se muestra el nombre.  
  
```cpp  
#include <string> #include <iostream> #include <iomanip> #include <filesystem> #include <chrono> #include <time.h> using namespace std; using namespace std::experimental::filesystem::v1; // Display the last write time for the file wstring LastWriteTimeToLocalTime(const path& file_path) { const auto last = chrono::system_clock::to_time_t(last_write_time(file_path)); tm timeinfo; localtime_s(&timeinfo, &last); wchar_t buf[56]; _wasctime_s(buf, 56, &timeinfo); // appends '\n' return wstring{ buf }; } // List files and directories in the specified path void DisplayFolderContents(const path& p) { wcout << L"Begin iterating " << p.wstring() << endl; for (const auto& entry : directory_iterator{ p }) { if (is_regular_file(entry.status())) { wcout << L" File: " << entry.path().filename() << " : " << LastWriteTimeToLocalTime(entry.path()); } else if (is_directory(entry.status())) { wcout << L" Dir: " << entry.path().filename() << endl; } } } void main() { wstring dir{ LR"(C:\users\public\documents\)" }; path p{ dir }; if (!is_directory(p)) { wcout << L"No such directory: " << dir << endl; return; } DisplayFolderContents(p); // IterateFolderRecursively(p); // see example wcout << endl << L"Press Enter to exit" << endl; wstring input; getline(wcin, input); }  
```  
  
### Iterar un árbol de directorios de manera recursiva  
 En el siguiente ejemplo se muestra cómo iterar un árbol de directorios de manera recursiva. Para ejecutar esta función, péguela en el ejemplo de código anterior después de la función DisplayFolderContents y quite la marca de comentario de la línea que la llama en main.  
  
```cpp  
// List files and directories recursively in the path void IterateFolderRecursively(const path& p) { wcout << L"Begin iterating " << p.wstring() << " recursively" << endl; for (recursive_directory_iterator it{ p }, end; it != end; ++it) { if (is_regular_file(it->status())) { wcout << setw(it.depth()) << L" " << L"File: " << it->path().filename() << L" : " << LastWriteTimeToLocalTime(it->path()); } else if (is_directory(it->status())) { wcout << setw(it.depth()) << L" " << L"Dir: " << it->path().filename() << endl; } } }  
```  
  
### Control de vínculos simbólicos  
 Al menos hasta Visual Studio 2015, la detección de vínculos simbólicos sigue sin ser compatible en Visual C\+\+.