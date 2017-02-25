---
title: "Advertencia del compilador (nivel 1) C4462 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4462"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4462"
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Advertencia del compilador (nivel 1) C4462
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no puede determinar el GUID del tipo.El programa puede dar un error en tiempo de ejecución.  
  
 La advertencia C4462 se produce en una aplicación o componente de Windows en tiempo de ejecución cuando uno de los parámetros de tipos de un controlador `TypedEventHandler` público es una referencia a la clase envolvente.  
  
 **Este tipo de código genera la advertencia:**  
  
```  
namespace N  
{  
       public ref struct EventArgs sealed {};  
       public ref struct R sealed  
       {  
              R() {}  
              event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
       };  
}  
  
[Platform::MTAThread]  
int main()  
{  
     auto x = ref new N::R();  
}  
  
```  
  
 **Para solucionar el error:**  
  
 Hay dos maneras de evitar el error.  Una de ellas, la que se muestra en el ejemplo siguiente, es proporcionar al evento accesibilidad interna, de modo que esté disponible para el código que se encuentra en el mismo ejecutable pero no para el código de otros componentes de Windows en tiempo de ejecución.  
  
```  
  
internal:  
event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
  
```  
  
 Si el evento tiene que ser público, puede utilizar la otra solución, que consiste en exponerlo a través de una interfaz predeterminada:  
  
```  
  
ref struct R;  
public interface struct IR { event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e; };  
  
public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR  
{  
    R() {}  
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;  
};  
  
```  
  
 Un GUID del tipo `Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^` solo se utiliza cuando se accede al tipo desde otro componente.  La primera solución funciona porque, tras implementarla, solo puede acceder dentro de su propio componente.  De lo contrario, el compilador tendría que presuponer el peor de los casos y emitir la advertencia.