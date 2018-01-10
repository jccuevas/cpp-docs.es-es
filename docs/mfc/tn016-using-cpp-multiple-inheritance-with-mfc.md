---
title: "TN016: Usar la herencia múltiple de C++ con MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.inheritance
dev_langs: C++
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b276e316ffc8ce04577532ac3b15400ee28f9f33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: Usar la herencia múltiple de C++ con MFC
Esta nota describe cómo usar la herencia múltiple (MI) con Microsoft Foundation Classes. El uso de MI no es necesario con MFC. MI no se utiliza en todas las clases MFC y no es necesario escribir una biblioteca de clases.  
  
 Los siguientes temas secundarios describen cómo MI afecta al uso de comunes giros de MFC, así como cubriendo algunas de las restricciones de MI. Algunas de estas restricciones son restricciones generales de C++. Otros son impuestos por la arquitectura de MFC.  
  
 Al final de esta nota técnica, encontrará una aplicación MFC completa que usa MI.  
  
## <a name="cruntimeclass"></a>CRuntimeClass  
 La persistencia y los mecanismos de creación de objeto dinámico de uso MFC el [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) estructura de datos para identificar las clases. MFC asocia a una de estas estructuras con cada clase dinámica o serializable en la aplicación. Estas estructuras se inicializan cuando se inicia la aplicación mediante el uso de un objeto estático especial de tipo `AFX_CLASSINIT`.  
  
 La implementación actual de `CRuntimeClass` no admite la información de tipo en tiempo de ejecución de MI. Esto no significa que no puede utilizar MI en la aplicación MFC. Sin embargo, tendrá ciertas responsabilidades cuando trabaje con objetos que tienen más de una clase base.  
  
 El [CObject:: IsKindOf](../mfc/reference/cobject-class.md#iskindof) método no determinará correctamente el tipo de un objeto, si tiene varias clases base. Por lo tanto, no puede usar [CObject](../mfc/reference/cobject-class.md) como una clase base virtual y todas las llamadas a `CObject` funciones miembro como [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize) y [CObject::operator nueva](../mfc/reference/cobject-class.md#operator_new)debe tener calificadores de ámbito para que C++ puede eliminar la ambigüedad de la llamada de función correspondiente. Cuando un programa usa MI en MFC, la clase que contiene el `CObject` clase base debe ser la clase del extremo izquierdo en la lista de clases base.  
  
 Una alternativa consiste en utilizar el `dynamic_cast` operador. Convertir un objeto con MI a uno de sus clases base, se forzará al compilador que utilice las funciones de la clase base proporcionada. Para obtener más información, consulte [dynamic_cast (operador)](../cpp/dynamic-cast-operator.md).  
  
## <a name="cobject---the-root-of-all-classes"></a>CObject - la raíz de todas las clases  
 Todas las clases importantes derivan directa o indirectamente de clase `CObject`. `CObject`Does no tiene ningún dato de miembro, pero tiene algunas funciones de forma predeterminada. Al utilizar MI, normalmente se heredan de dos o más `CObject`-las clases derivadas. En el ejemplo siguiente se muestra cómo una clase puede heredar de un [CFrameWnd](../mfc/reference/cframewnd-class.md) y un [CObList](../mfc/reference/coblist-class.md):  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
 ...  
};  
CListWnd myListWnd;  
```  
  
 En este caso `CObject` se incluye dos veces. Esto significa que necesita una manera de eliminar la ambigüedad de cualquier referencia a `CObject` métodos u operadores. El `operator new` y [operador delete](../mfc/reference/cobject-class.md#operator_delete) son dos operadores que deben eliminar la ambigüedad. Como otro ejemplo, el código siguiente provoca un error en tiempo de compilación:  
  
```  
myListWnd.Dump(afxDump);
*// compile time error, CFrameWnd::Dump or CObList::Dump   
```  
  
## <a name="reimplementing-cobject-methods"></a>Volviendo a implementar métodos de CObject  
 Cuando se crea una nueva clase que tiene dos o más `CObject` derivadas de las clases base, debe volver a implementar el `CObject` métodos que desea que otros usuarios puedan usar. Operadores `new` y `delete` son obligatorios y [volcar](../mfc/reference/cobject-class.md#dump) se recomienda. El reimplements de ejemplo siguiente la `new` y `delete` operadores y `Dump` método:  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
public:  
    void* operator new(size_t nSize)  
 { return CFrameWnd:: operator new(nSize);

}  
    void operator delete(void* p)  
 { CFrameWnd:: operator delete(p);

}  
 
    void Dump(CDumpContent& dc)  
 { CFrameWnd::Dump(dc);

    CObList::Dump(dc);

} 
 ...  
};  
```  
  
## <a name="virtual-inheritance-of-cobject"></a>Herencia virtual de CObject  
 Podría parecer que heredar prácticamente `CObject` podría solucionar el problema de ambigüedad de función, pero que no es el caso. Porque no hay ningún dato de miembro en `CObject`, no es necesario herencia virtual para evitar que varias copias de los datos de miembro de clase base. En el primer ejemplo que se mostró anteriormente, el `Dump` método virtual es sigue siendo ambiguo porque se implementa de forma distinta en `CFrameWnd` y `CObList`. La mejor manera de evitar la ambigüedad es seguir las recomendaciones que se presentan en la sección anterior.  
  
## <a name="cobjectiskindof-and-run-time-typing"></a>CObject:: IsKindOf y escriba el tiempo de ejecución  
 El mecanismo de tipo de tiempo de ejecución compatible con MFC en `CObject` utiliza las macros `DECLARE_DYNAMIC`, `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE`, `IMPLEMENT_DYNCREATE`, `DECLARE_SERIAL` y `IMPLEMENT_SERIAL`. Estas macros pueden realizar una comprobación de tipo en tiempo de ejecución para garantizar las conversiones de restricción seguro.  
  
 Estas macros admiten una sola clase base y funcionarán en una forma limitada para las clases heredadas multiplicar. La clase base se especifica en `IMPLEMENT_DYNAMIC` o `IMPLEMENT_SERIAL` debería ser la clase base del primer (o más a la izquierda). Esta ubicación le permitirá la comprobación para el extremo izquierdo base sólo en una clase de tipo. El sistema de tipos de tiempo de ejecución sepa nada acerca de las clases base adicionales. En el ejemplo siguiente, los sistemas de tiempo de ejecución hará escriba comprobación contra `CFrameWnd`, pero sepa nada acerca de `CObList`.  
  
```  
class CListWnd : public CFrameWnd,
    public CObList  
{  
    DECLARE_DYNAMIC(CListWnd) 
 ...  
};  
IMPLEMENT_DYNAMIC(CListWnd,
    CFrameWnd)  
```  
  
## <a name="cwnd-and-message-maps"></a>CWnd y mapas de mensajes  
 Para que el sistema de asignación de mensajes MFC para que funcione correctamente, hay dos requisitos adicionales:  
  
-   Debe haber sólo uno `CWnd`-derivado de la clase base.  
  
-   El `CWnd`-clase derivada debe ser la clase base del primer (o más a la izquierda).  
  
 Estos son algunos ejemplos que no funcionan:  
  
```  
class CTwoWindows : public CFrameWnd,
    public CEdit  
 { ... }; *// error : two copies of CWnd  
 
class CListEdit : public CObList,
    public CEdit  
 { ... }; *// error : CEdit (derived from CWnd) must be first  
```  
  
## <a name="a-sample-program-using-mi"></a>Un programa de ejemplo con MI  
 El ejemplo siguiente es una aplicación independiente que consta de una clase derivada de `CFrameWnd` y [CWinApp](../mfc/reference/cwinapp-class.md). No se recomienda que estructurar una aplicación de esta manera, pero este es un ejemplo de la aplicación MFC más pequeño que tiene una clase.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

