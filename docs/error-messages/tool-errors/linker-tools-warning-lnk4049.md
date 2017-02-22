---
title: "Advertencia de las herramientas del vinculador LNK4049 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4049"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4049"
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# Advertencia de las herramientas del vinculador LNK4049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se importó el símbolo 'símbolo' definido localmente  
  
 El símbolo se exportó e importó al mismo tiempo al programa.  
  
 El vinculador genera esta advertencia cuando se declara un símbolo utilizando el atributo de clase de almacenamiento `__declspec(dllexport)` en un archivo objeto y se hace referencia al mismo utilizando el atributo utilizando el atributo `__declspec(dllimport)` en otro archivo objeto.  
  
 La advertencia LNK4049 es una versión más general de [Advertencia de las herramientas del vinculador LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md).  El vinculador genera la advertencia LNK4049 cuando no puede determinar desde qué función se hizo referencia el símbolo importado.  
  
 Los casos más habituales en los que se genera la advertencia LNK4049 en lugar de LNK4217 son los siguientes:  
  
-   Realización de una vinculación incremental mediante la opción [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md).  
  
-   Realización de una optimización de todo el programa mediante la opción [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 Para solucionarlo, pruebe una de las acciones siguientes:  
  
-   Quite la declaración de nombre `__declspec(dllimport)` de la declaración adelantada del símbolo que desencadenó la advertencia LNK4049.  Puede buscar los símbolos dentro de una imagen binaria con la utilidad **DUMPBIN**.  El modificador **DUMPBIN \/SYMBOLS** muestra la tabla de símbolos COFF de la imagen.  Para obtener más información acerca de la utilidad **DUMPBIN**, vea [Referencia de DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
-   Deshabilite temporalmente la vinculación incremental y la optimización de todo el programa.  Al volver a compilar la aplicación, se generará la advertencia LNK4217, que incluirá el nombre de la función desde la que se hizo referencia al símbolo importado.  Quite la declaración `__declspec(dllimport)` del símbolo importado y habilite vinculación incremental o la optimización de todo el programa, según convenga.  
  
 Aunque el código final generado se comportará correctamente, el código generado para llamar a la función importada resulta menos eficaz que llamar directamente a la función.  Esta advertencia no aparecerá cuando se compile con la opción [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Para obtener más información sobre las declaraciones de datos de importación y exportación, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).  
  
## Ejemplo  
 Al vincular los dos módulos siguientes, se generará la advertencia LNK4049.  El primer módulo genera un archivo objeto que contiene una única función exportada.  
  
```  
// LNK4049a.cpp  
// compile with: /c  
  
__declspec(dllexport) int func()   
{  
   return 3;  
}  
```  
  
## Ejemplo  
 El segundo módulo genera un archivo objeto que contiene una declaración adelantada a la función exportada del primer módulo, junto con una llamada a esta función dentro de la función `main`.  Al vincular este módulo con el primer módulo, se generará la advertencia LNK4049.  Al quitar la declaración `__declspec(dllimport)`, se resolverá la advertencia.  
  
```  
// LNK4049b.cpp  
// compile with: /link /WX /LTCG LNK4049a.obj  
// LNK4049 expected  
  
__declspec(dllimport) int func();  
// try the following line instead  
// int func();  
  
int main()  
{  
   return func();  
}  
```  
  
## Vea también  
 [Advertencia de las herramientas del vinculador LNK4217](../../error-messages/tool-errors/linker-tools-warning-lnk4217.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)