---
title: "GetProcAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProcAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], GetProcAddress"
  - "GetProcAddress (método)"
  - "exportaciones de ordinales [C++]"
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# GetProcAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los procesos que se vinculan explícitamente a un archivo DLL llaman a [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) para obtener la dirección de una función exportada del archivo DLL.  Debe utilizar el puntero a la función devuelto para llamar a la función del archivo DLL.  **GetProcAddress** toma como parámetros el identificador de módulo del archivo DLL \(devuelto por **LoadLibrary**, `AfxLoadLibrary` o **GetModuleHandle**\) y toma el nombre de la función a la que se desea llamar o el ordinal de exportación de la función.  
  
 Como está llamando a la función DLL mediante un puntero y no hay comprobación de tipos en tiempo de compilación, debe asegurarse de que los parámetros pasados a la función son correctos, para no sobrepasar la memoria asignada en la pila y causar así una infracción de acceso.  Una forma de contribuir a la seguridad de tipos es consultar los prototipos de función de las funciones exportadas y crear definiciones typedef coincidentes para los punteros de función.  Por ejemplo:  
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 La forma de especificar la función que desea al llamar a **GetProcAddress** dependerá de cómo se compiló el archivo DLL.  
  
 Sólo podrá obtener el ordinal de exportación si el archivo DLL al que se está vinculando se ha creado con un archivo de definición de módulos \(.def\) y si los ordinales figuran en la lista de funciones de la sección **EXPORTS** del archivo .def correspondiente al archivo DLL.  Utilizar un ordinal de exportación en lugar de un nombre de función para llamar a **GetProcAddress** resulta un poco más rápido si el archivo DLL tiene muchas funciones exportadas, puesto que los ordinales exportados sirven como índices en la tabla de exportación del archivo DLL.  Con un ordinal de exportación, **GetProcAddress** puede encontrar la función directamente, sin tener que comparar el nombre especificado con los nombres de función de la tabla de exportación del archivo DLL.  Sin embargo, sólo se debe llamar a **GetProcAddress** con un ordinal de exportación si se dispone de control sobre la asignación de ordinales a las funciones exportadas en el archivo .def.  
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma implícita](../build/linking-implicitly.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [\<caps:sentence id\="tgt17" sentenceid\="8c920606bb67e2587dd3c3e5cf977593" class\="tgtSentence"\>FreeLibrary\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [Exportar desde un archivo DLL mediante archivos DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)