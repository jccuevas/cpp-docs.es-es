---
title: "Vinculaci&#243;n expl&#237;cita | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vinculación explícita [C++]"
ms.assetid: 1e13d960-a195-4e6d-9864-7d8f3a701f4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Vinculaci&#243;n expl&#237;cita
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con la vinculación explícita, las aplicaciones deben realizar una llamada a función para cargar explícitamente el archivo DLL en tiempo de ejecución.  Para una vinculación explícita a un archivo DLL, una aplicación debe:  
  
-   Llamar a **LoadLibrary** \(o a una función similar\) para cargar el archivo DLL y obtener un identificador de módulo.  
  
-   Llamar a **GetProcAddress** para obtener un puntero a función para cada función exportada a la que la aplicación desee llamar.  Como las aplicaciones llaman a las funciones del archivo DLL mediante un puntero, el compilador no genera referencias externas, por lo que no hay necesidad de vincularse a una biblioteca de importación.  
  
-   Llamar a **FreeLibrary** cuando se haya acabado de utilizar el archivo DLL.  
  
 Por ejemplo:  
  
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
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma implícita](../build/linking-implicitly.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
-   [FreeLibrary y AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [La ruta de acceso de búsqueda que Windows utiliza para buscar una DLL](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
## Vea también  
 [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)