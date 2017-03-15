---
title: "TN016: Usar la herencia m&#250;ltiple de C++ con MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MI (herencia múltiple)"
  - "herencia múltiple, compatibilidad con MFC para"
  - "TN016"
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
caps.latest.revision: 22
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN016: Usar la herencia m&#250;ltiple de C++ con MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe cómo utilizar la herencia múltiple \(MI\) con Microsoft Foundation Classes.  El uso de MI no se requiere con MFC.  El MI no se utiliza en las clases de MFC y no es necesario escribir una biblioteca de clases.  
  
 Los subtemas siguientes describen cómo el MI afecta al uso de las idioms comunes de MFC así como se ofrecen algunas de las restricciones de my.  Algunas de estas restricciones son restricciones general de C\+\+.  Otros son impuestos por la arquitectura de MFC.  
  
 Al final de esta nota técnica encontrará una aplicación MFC completa que utilice el my.  
  
## Recursos  
 La persistencia y los mecanismos dinámicos de la creación de objetos MFC utilizan la estructura de datos de [Recursos](../mfc/reference/cruntimeclass-structure.md) para identificar clases.  MFC asocia una de estas estructuras a cada clase dinámica y\/o serializables en la aplicación.  Inicializar estas estructuras cuando se inicia la aplicación utilizando un objeto estático especial de `AFX_CLASSINIT`escrito.  
  
 La implementación actual de `CRuntimeClass` no admite la información de tipo en tiempo de ejecución de my.  Esto no significa que no puede usar MI en la aplicación MFC.  Sin embargo, tendrá ciertas responsabilidades cuando se trabaja con los objetos que tienen más de una clase base.  
  
 El método de [CObject::IsKindOf](../Topic/CObject::IsKindOf.md) correctamente no determinará el tipo de un objeto si tiene varias clases base.  Por consiguiente, no puede utilizar [CObject](../mfc/reference/cobject-class.md) como clase base virtual, y todas las llamadas a las funciones miembro de `CObject` como [CObject::Serialize](../Topic/CObject::Serialize.md) y a [CObject::operator new](../Topic/CObject::operator%20new.md) deben tener calificadores de ámbito de modo que C\+\+ puede eliminar la ambigüedad de la llamada de función adecuada.  Cuando un programa utiliza el MI dentro de MFC, la clase que contiene la clase base de `CObject` debe ser la clase a la izquierda en la lista de clases base.  
  
 Una alternativa es usar el operador de `dynamic_cast` .  Convertir un objeto con el MI a una de sus clases base también el compilador para utilizar funciones en la clase base proporcionada.  Para obtener más información, vea [dynamic\_cast \(Operador\)](../cpp/dynamic-cast-operator.md).  
  
## Raíz de CObject \- de todas las clases  
 Todas las clases significativas deriva directa o indirectamente de la clase `CObject`.  `CObject` no tiene datos de miembros, pero tiene cierta funcionalidad predeterminada.  Cuando se utiliza el MI, heredará normalmente a partir de dos o más `CObject`\- clases derivadas.  El ejemplo siguiente se muestra cómo una clase puede heredar de [CFrameWnd](../mfc/reference/cframewnd-class.md) y de [CObList](../mfc/reference/coblist-class.md):  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
 ...  
};  
CListWnd myListWnd;  
```  
  
 En este caso `CObject` es dos veces incluidas.  Esto significa que necesita una manera de eliminar la ambigüedad de las referencias a los métodos o los operadores de `CObject` .  `operator new` y [operador delete](../Topic/CObject::operator%20delete.md) son dos operadores que se deben quitar ambigüedades.  Otro ejemplo, el código siguiente provoca un error en tiempo de compilación:  
  
```  
myListWnd.Dump(afxDump);  
    // compile time error, CFrameWnd::Dump or CObList::Dump ?  
```  
  
## Métodos de Reimplementing CObject  
 Cuando se crea una nueva clase que tiene dos o más clases base derivadas `CObject` , debe volver a implementar los métodos de `CObject` que desee a otras personas para utilizar.  Los operadores `new` y `delete` son obligatorios y se recomienda [Volcado](../Topic/CObject::Dump.md) .  Los reimplements siguientes de ejemplo los operadores de `new` y de `delete` y el método de `Dump` :  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
public:  
    void* operator new(size_t nSize)  
        { return CFrameWnd::operator new(nSize); }  
    void operator delete(void* p)  
        { CFrameWnd::operator delete(p); }  
  
    void Dump(CDumpContent& dc)  
        { CFrameWnd::Dump(dc);  
          CObList::Dump(dc); }  
     ...  
};  
```  
  
## Herencia virtual de CObject  
 Puede parecer que la herencia de `CObject` solucionaría el problema de la ambigüedad de la función, pero no es el caso.  Porque no hay datos de miembros en `CObject`, no necesita herencia virtual evitar varias copias de los datos de miembro de clase base.  En el primer ejemplo que se ha mostrado anteriormente, el método virtual de `Dump` todavía es ambigua porque se implementa de manera diferente en `CFrameWnd` y `CObList`.  La mejor manera de ambigüedad es seguir las recomendaciones mostradas en la sección anterior.  
  
## CObject::IsKindOf y escritura en tiempo de ejecución  
 El tiempo de ejecución que escribe el mecanismo compatible con MFC en `CObject` utiliza las macros `DECLARE_DYNAMIC`, `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE`, `IMPLEMENT_DYNCREATE`, `DECLARE_SERIAL` y `IMPLEMENT_SERIAL`.  Estas macros pueden realizar una comprobación de tipo en tiempo de ejecución para garantizar los abatimientos seguros.  
  
 Estas macros admiten solo una clase base y funcionan de forma limitada para multiplican clases heredadas.  La clase base que se especifica en `IMPLEMENT_DYNAMIC` o `IMPLEMENT_SERIAL` debe ser la primera \(o de izquierda\) clase base.  Esta posición le permite que la comprobación de tipos para la clase base de izquierda únicamente.  El sistema de tipos en tiempo de ejecución no conocerá nada sobre clases base adicionales.  En el ejemplo siguiente, los sistemas en tiempo de ejecución harán comprobación de tipos con `CFrameWnd`, pero no conocerán nada sobre `CObList`.  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
    DECLARE_DYNAMIC(CListWnd)  
    ...  
};  
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)  
```  
  
## CWnd y mapas de mensajes  
 Para que el sistema del mapa de mensajes MFC funcione correctamente, hay dos requisitos adicionales:  
  
-   Debe haber un `CWnd`\- clase base derivada.  
  
-   `CWnd`\- clase base derivada debe ser la primera \(o de izquierda\) clase base.  
  
 A continuación se muestran algunos ejemplos que no funcionarán:  
  
```  
class CTwoWindows : public CFrameWnd, public CEdit  
    { ... };  
        // error : two copies of CWnd  
  
class CListEdit : public CObList, public CEdit  
    { ... };  
        // error : CEdit (derived from CWnd) must be first  
```  
  
## Un programa de ejemplo mediante MI  
 El ejemplo siguiente es una aplicación independiente que consta de una clase derivada de `CFrameWnd` y de [CWinApp](../mfc/reference/cwinapp-class.md).  No se recomienda estructura una aplicación de esta manera, pero éste es un ejemplo de aplicación MFC menor que tiene una clase.  
  
```  
#include <afxwin.h>  
  
class CHelloAppAndFrame : public CFrameWnd, public CWinApp  
{   
public:  
    CHelloAppAndFrame()  
        { }  
  
    // Necessary because of MI disambiguity  
    void* operator new(size_t nSize)  
        { return CFrameWnd::operator new(nSize); }  
    void operator delete(void* p)  
        { CFrameWnd::operator delete(p); }  
  
    // Implementation  
    // CWinApp overrides  
    virtual BOOL InitInstance();  
    // CFrameWnd overrides  
    virtual void PostNcDestroy();  
    afx_msg void OnPaint();  
  
    DECLARE_MESSAGE_MAP()  
  
};  
  
BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)  
    ON_WM_PAINT()  
END_MESSAGE_MAP()  
  
// because the frame window is not allocated on the heap, we must  
// override PostNCDestroy not to delete the frame object  
void CHelloAppAndFrame::PostNcDestroy()  
{  
    // do nothing (do not call base class)  
}  
  
void CHelloAppAndFrame::OnPaint()  
{  
    CPaintDC dc(this);  
    CRect rect;  
    GetClientRect(rect);  
  
    CString s = "Hello, Windows!";  
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);  
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));  
    dc.SetBkMode(TRANSPARENT);  
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);  
}  
  
// Application initialization  
BOOL CHelloAppAndFrame::InitInstance()  
{  
    // first create the main frame  
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",  
        WS_OVERLAPPEDWINDOW, rectDefault))  
        return FALSE;  
  
    // the application object is also a frame window  
    m_pMainWnd = this;            
    ShowWindow(m_nCmdShow);  
    return TRUE;  
}  
  
CHelloAppAndFrame theHelloAppAndFrame;  
```  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)