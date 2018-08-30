---
title: Control y E/s de archivos (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d04f918c9c92c2de8ff6b654a8a0d4ee43c2130
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196030"
---
# <a name="file-handling-and-io-ccli"></a>Control y E/S de archivos (C++/CLI)
Muestra distintas operaciones de archivo mediante .NET Framework.  
  
 Los temas siguientes muestran el uso de las clases definidas en el <xref:System.IO> espacio de nombres para llevar a cabo varias operaciones de archivo.  
  
## <a name="enumerate"></a> Enumerar archivos en un directorio
En el ejemplo de código siguiente se muestra cómo recuperar una lista de los archivos en un directorio. Además, se enumeran los subdirectorios. El siguiente ejemplo de código utiliza el <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> y <xref:System.IO.Directory.GetDirectories%2A> métodos para mostrar el contenido del directorio C:\Windows.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// enum_files.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ folder = "C:\\";  
   array<String^>^ dir = Directory::GetDirectories( folder );  
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);  
   for (int i=0; i<dir->Length; i++)  
      Console::WriteLine(dir[i]);  
  
   array<String^>^ file = Directory::GetFiles( folder );  
   Console::WriteLine("--== Files inside '{0}' ==--", folder);  
   for (int i=0; i<file->Length; i++)  
      Console::WriteLine(file[i]);  
  
   return 0;  
}  
```  

## <a name="monitor"></a> Cambios del sistema de archivos de Monitor
El siguiente ejemplo de código usa <xref:System.IO.FileSystemWatcher> para registrar eventos correspondientes a archivos creados, modificados, eliminado o cuyo nombre ha cambiado. En lugar de sondear periódicamente un directorio para los cambios en archivos, puede usar el <xref:System.IO.FileSystemWatcher> clase para desencadenar eventos cuando se detecta un cambio.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// monitor_fs.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::IO;  
  
ref class FSEventHandler  
{  
public:  
    void OnChanged (Object^ source, FileSystemEventArgs^ e)  
    {  
        Console::WriteLine("File: {0} {1}",   
               e->FullPath, e->ChangeType);  
    }  
    void OnRenamed(Object^ source, RenamedEventArgs^ e)  
    {  
        Console::WriteLine("File: {0} renamed to {1}",   
                e->OldFullPath, e->FullPath);  
    }  
};  
  
int main()  
{  
   array<String^>^ args = Environment::GetCommandLineArgs();  
  
   if(args->Length < 2)  
   {  
      Console::WriteLine("Usage: Watcher.exe <directory>");  
      return -1;  
   }  
  
   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );  
   fsWatcher->Path = args[1];  
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>   
              (NotifyFilters::FileName |   
               NotifyFilters::Attributes |   
               NotifyFilters::LastAccess |   
               NotifyFilters::LastWrite |   
               NotifyFilters::Security |   
               NotifyFilters::Size );  
  
    FSEventHandler^ handler = gcnew FSEventHandler();   
    fsWatcher->Changed += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Created += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Deleted += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Renamed += gcnew RenamedEventHandler(   
            handler, &FSEventHandler::OnRenamed);  
  
    fsWatcher->EnableRaisingEvents = true;  
  
    Console::WriteLine("Press Enter to quit the sample.");  
    Console::ReadLine( );  
}  
```  

## <a name="read_binary"></a> Leer un archivo binario
El ejemplo de código siguiente muestra cómo leer datos binarios de un archivo, mediante el uso de dos clases desde el <xref:System.IO?displayProperty=fullName> espacio de nombres: <xref:System.IO.FileStream> y <xref:System.IO.BinaryReader>. <xref:System.IO.FileStream> representa al propio archivo. <xref:System.IO.BinaryReader> Proporciona una interfaz a la secuencia que permite el acceso binario.  
  
 El ejemplo de código lee un archivo denominado data.bin y contiene enteros en formato binario. Para obtener información sobre este tipo de archivo, vea [Cómo: escribir un archivo binario (C++ / c++ / CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// binary_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "data.bin";  
   try  
   {  
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);  
      BinaryReader^ br = gcnew BinaryReader(fs);  
  
      Console::WriteLine("contents of {0}:", fileName);  
      while (br->BaseStream->Position < br->BaseStream->Length)  
         Console::WriteLine(br->ReadInt32().ToString());  
  
      fs->Close( );  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("File '{0}' not found", fileName);  
      else  
         Console::WriteLine("Exception: ({0})", e);  
      return -1;  
   }  
   return 0;  
}  
```  
## <a name="read_text"></a> Leer un archivo de texto
El código siguiente muestra cómo abrir y leer un archivo de texto de línea a la vez, mediante la <xref:System.IO.StreamReader> clase que se define en el <xref:System.IO?displayProperty=fullName> espacio de nombres. Una instancia de esta clase se utiliza para abrir un archivo de texto y, a continuación, el <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> método se usa para recuperar cada línea.  
  
 Este ejemplo de código lee un archivo denominado textfile.txt y contiene texto. Para obtener información sobre este tipo de archivo, vea [Cómo: escribir un archivo de texto (C++ / c++ / CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  

## <a name="retrieve"></a> Recuperar información de archivo 
En el ejemplo de código siguiente, se muestra la clase <xref:System.IO.FileInfo>. Cuando se tiene el nombre de un archivo, se puede utilizar esta clase para recuperar información sobre el archivo como, por ejemplo, tamaño, directorio, nombre completo, y fecha y hora de su creación y de la última modificación.  
  
 Este código recupera información del archivo para Notepad.exe.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// file_info.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<String^>^ args = Environment::GetCommandLineArgs();  
   if (args->Length < 2)  
   {  
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");  
      return -1;  
   }  
  
   FileInfo^ fi = gcnew FileInfo( args[1] );  
  
   Console::WriteLine("file size: {0}", fi->Length );  
  
   Console::Write("File creation date:  ");  
   Console::Write(fi->CreationTime.Month.ToString());  
   Console::Write(".{0}", fi->CreationTime.Day.ToString());  
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());  
  
   Console::Write("Last access date:  ");  
   Console::Write(fi->LastAccessTime.Month.ToString());  
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());  
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());  
  
   return 0;  
}  
```  

## <a name="write_binary"></a> Escribir un archivo binario
En el siguiente ejemplo de código se muestra cómo escribir datos binarios en un archivo. Se usan dos clases del espacio de nombres <xref:System.IO>: <xref:System.IO.FileStream> y <xref:System.IO.BinaryWriter>. La clase <xref:System.IO.FileStream> representa al propio archivo, mientras que la clase <xref:System.IO.BinaryWriter> proporciona una interfaz a la secuencia que permite el acceso binario.  
  
 En el siguiente ejemplo de código se escribe un archivo que contiene enteros en formato binario. Este archivo puede leerse con el código de [Cómo: leer un archivo binario (C++ / c++ / CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md).  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  

## <a name="write_text"></a> Escribir un archivo de texto
En el ejemplo de código siguiente se muestra cómo crear un archivo de texto y escribir texto en él mediante el <xref:System.IO.StreamWriter> (clase), que se define en el <xref:System.IO> espacio de nombres. El <xref:System.IO.StreamWriter> constructor toma el nombre del archivo que se va a crear. Si el archivo existe, se sobrescribe (a menos que pase True como segundo <xref:System.IO.StringWriter> argumento de constructor).  
  
 Después, se almacena el archivo mediante el <xref:System.IO.StreamWriter.Write%2A> y <xref:System.IO.TextWriter.WriteLine%2A> funciones.  
  
### <a name="example"></a>Ejemplo  
  
```cpp  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  

## <a name="see-also"></a>Vea también   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

 [E/S de archivos y secuencias](https://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)

 [Espacio de nombres System.IO](https://msdn.microsoft.com/library/system.io.aspx)