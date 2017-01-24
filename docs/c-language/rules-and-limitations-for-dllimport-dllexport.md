---
title: "Reglas y limitaciones para dllimport/dllexport | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "dllexport (atributo) [C++]"
  - "dllexport (atributo) [C++], limitaciones y reglas"
  - "dllimport (atributo) [C++], limitaciones y reglas"
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Reglas y limitaciones para dllimport/dllexport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
-   Si declara una función sin el atributo **dllimport** o `dllexport`, la función no se considera parte de la interfaz DLL.  Por consiguiente, la definición de la función debe estar presente en ese módulo o en otro módulo del mismo programa.  Para que una función forme parte de la interfaz DLL, debe declarar la definición de la función en el otro módulo como `dllexport`.  Si no, se genera un error del vinculador cuando se compila el cliente.  
  
-   Si un solo módulo del programa contiene declaraciones **dllimport** y `dllexport` para la misma función, el atributo `dllexport` tiene prioridad sobre el atributo **dllimport**.  Sin embargo, se genera una advertencia del compilador.  Por ejemplo:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllExport void func1( void );   /* Warning; dllexport */  
                                       /* takes precedence. */  
  
    ```  
  
-   No se puede inicializar un puntero de datos estáticos con la dirección de un objeto de datos declarado con el atributo **dllimport**.  Por ejemplo, el siguiente código genera errores:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport int i;  
       .  
       .  
       .  
       int *pi = &i;                           /* Error */  
  
       void func2()  
       {  
          static int *pi = &i;                   /* Error */  
       }  
  
    ```  
  
-   Al inicializar un puntero a función estático con la dirección de una función declarada con **dllimport**, se establece el puntero en la dirección del código thunk de importación de DLL \(código auxiliar que transfiere el control a la función\) en lugar de la dirección de la función.  Esta asignación no genera un mensaje de error:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void   
       .  
       .  
       .  
       static void ( *pf )( void ) = &func1;   /* No Error */  
  
       void func2()  
       {  
          static void ( *pf )( void ) = &func1;  /* No Error */  
       }  
  
    ```  
  
-   Puesto que un programa que incluya el atributo `dllexport` en la declaración de un objeto debe proporcionar la definición de ese objeto, puede inicializar un puntero a función estático global o local con la dirección de una función `dllexport`.  De igual forma, puede inicializar un puntero de datos estático global o local con la dirección de un objeto de datos `dllexport`.  Por ejemplo:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllImport int i;  
  
       DllExport void func1( void );  
       DllExport int i;  
       .  
       .  
       .  
       int *pi = &i;                            /* Okay */  
       static void ( *pf )( void ) = &func1;    /* Okay */  
  
       void func2()  
       {  
          static int *pi = i;                     /* Okay */  
          static void ( *pf )( void ) = &func1;   /* Okay */  
       }  
  
    ```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Funciones de importación y exportación de archivos DLL](../c-language/dll-import-and-export-functions.md)