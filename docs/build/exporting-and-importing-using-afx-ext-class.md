---
title: Exportar e importar mediante AFX_EXT_CLASS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afx_ext_class
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cc853c66afae72d6e426d800c0443ab206ab20
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-and-importing-using-afxextclass"></a>Exportar e importar mediante AFX_EXT_CLASS  
  
[DLL de extensión MFC](../build/extension-dlls-overview.md) , use la macro **AFX_EXT_CLASS** para exportar clases; los archivos ejecutables que se vinculan a la DLL de extensión MFC utilizan la macro para importar las clases de. Con el **AFX_EXT_CLASS** (macro), los mismos archivos de encabezado que se utilizan para generar el archivo DLL puede utilizarse con los archivos ejecutables que se vinculan al archivo DLL de extensión de MFC.  
  
 En el archivo de encabezado para el archivo DLL, agregue el **AFX_EXT_CLASS** palabra clave a la declaración de la clase como sigue:  
  
```cpp  
class AFX_EXT_CLASS CMyClass : public CDocument  
{  
// <body of class>  
};  
```  
  
Esta macro se define por MFC como `__declspec(dllexport)` cuando los símbolos de preprocesador `_AFXDLL` y `_AFXEXT` se definen. Pero la macro se define como `__declspec(dllimport)` cuando `_AFXDLL` se define y `_AFXEXT` no está definido. Cuando se define el símbolo de preprocesador `_AFXDLL` indica que la versión compartida de MFC está siendo utilizada por el archivo ejecutable de destino (un archivo DLL o una aplicación). Cuando ambos `_AFXDLL` y `_AFXEXT` están definidos, esto indica que el archivo ejecutable de destino es un archivo DLL de extensión MFC.  
  
Dado que `AFX_EXT_CLASS` se define como `__declspec(dllexport)` al exportar desde un archivo DLL de extensión MFC, pueden exportar clases completas sin colocar los nombres representativos para todos los símbolos de dicha clase en el archivo .def.  
  
Aunque puede evitar la creación de un archivo .def y todos los nombres representativos para la clase con este método, la creación de un archivo .def es más eficaz porque los nombres se pueden exportar por ordinal. Para utilizar el método del archivo .def de exportar, coloque el código siguiente al principio y al final del archivo de encabezado:  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
> [!CAUTION]
>  Tenga cuidado al exportar funciones inline, ya que podrían producir la posibilidad de conflictos de versiones. Una función inline se expande para crear el código de aplicación; por lo tanto, si más adelante vuelve a escribir la función, se no se actualiza a menos que se vuelva a compilar la aplicación en Sí. Normalmente, funciones de archivos DLL pueden actualizarse sin volver a generar las aplicaciones que las utilizan.  
  
## <a name="exporting-individual-members-in-a-class"></a>Exportar a miembros individuales de una clase  
  
En ocasiones, puede exportar a miembros individuales de la clase. Por ejemplo, si va a exportar una `CDialog`-clase derivada, solo deberá exportar el constructor y el `DoModal` llamar. Puede usar `AFX_EXT_CLASS` en los miembros individuales que desea exportar.  
  
Por ejemplo:  
  
```cpp  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   ...  
   // rest of class definition  
   ...  
};  
```  
  
Dado que ya no se va a exportar a todos los miembros de la clase, puede encontrarse con un problema adicional debido al modo en que funcionan las macros MFC. Algunas de las macros de aplicación auxiliar de MFC realmente declaran ni definen a miembros de datos. Por lo tanto, también deben exportarse estos miembros de datos desde el archivo DLL.  
  
Por ejemplo, el `DECLARE_DYNAMIC` macro se define como sigue cuando se crea un archivo DLL de extensión MFC:  
  
```cpp  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
La línea que comienza con estático `AFX_DATA` se declara como un objeto estático dentro de la clase. Para exportar correctamente esta clase y tener acceso a la información de tiempo de ejecución desde un aplicación cliente, debe exportar este objeto estático. Porque el objeto estático se declara con el modificador `AFX_DATA`, basta con definir `AFX_DATA` como `__declspec(dllexport)` al generar el archivo DLL y definirlo como `__declspec(dllimport)` al generar el archivo ejecutable del cliente. Dado que `AFX_EXT_CLASS` ya está definida de esta manera, solo tiene que volver a definir `AFX_DATA` a ser el mismo que `AFX_EXT_CLASS` alrededor de la definición de clase.  
  
Por ejemplo:  
  
```cpp  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
  
class CExampleView : public CView  
{  
   DECLARE_DYNAMIC()  
   // ... class definition ...  
};  
  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
Dado que MFC siempre utiliza el `AFX_DATA` símbolos en elementos de datos define dentro de las macros, esto funciona técnica para todos estos escenarios. Por ejemplo, funciona para `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Si va a exportar toda la clase en lugar de los miembros seleccionados de la clase, se exportan automáticamente los miembros de datos estáticos.  
  
### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
-   [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Exportar funciones de C para utilizarlas en ejecutables de C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Nombres representativos](../build/reference/decorated-names.md)  
  
-   [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importaciones mutuas](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Vea también  
 [Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)