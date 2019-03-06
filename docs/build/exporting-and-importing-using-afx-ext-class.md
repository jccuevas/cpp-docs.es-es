---
title: Exportar e importar mediante AFX_EXT_CLASS
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 1451b452c5e2dc62e83e5b8f473248fa7c231877
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421199"
---
# <a name="exporting-and-importing-using-afxextclass"></a>Exportar e importar mediante AFX_EXT_CLASS

[DLL de extensión MFC](../build/extension-dlls-overview.md) utilizar la macro **AFX_EXT_CLASS** exportar clases; los archivos ejecutables que se vinculan a la DLL de extensión MFC utilizan la macro para importar las clases. Con el **AFX_EXT_CLASS** (macro), los mismos archivos de encabezado que se usan para generar el archivo DLL se puede usar con los archivos ejecutables que vinculen a la DLL de extensión de MFC.

En el archivo de encabezado para el archivo DLL, agregue el **AFX_EXT_CLASS** palabra clave a la declaración de la clase como sigue:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Esta macro se define por MFC como `__declspec(dllexport)` cuando los símbolos de preprocesador `_AFXDLL` y `_AFXEXT` se definen. Pero la macro se define como `__declspec(dllimport)` cuando `_AFXDLL` se define y `_AFXEXT` no está definido. Cuando se define el símbolo de preprocesador `_AFXDLL` indica que la versión compartida de MFC está siendo utilizada por el archivo ejecutable de destino (un archivo DLL o una aplicación). Cuando ambos `_AFXDLL` y `_AFXEXT` están definidos, esto indica que el archivo ejecutable de destino es un archivo DLL de extensión MFC.

Dado que `AFX_EXT_CLASS` se define como `__declspec(dllexport)` al exportar desde un archivo DLL de extensión MFC, puede exportar clases completas sin colocar los nombres representativos para todos los símbolos de la clase en el archivo. def.

Aunque puede evitar la creación de un archivo .def y todos los nombres representativos para la clase con este método, la creación de un archivo .def es más eficaz porque los nombres se pueden exportar por ordinal. Para usar el método del archivo .def de exportación, coloque el código siguiente al principio y al final del archivo de encabezado:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
>  Tenga cuidado al exportar funciones inline, ya que podrían producir la posibilidad de conflictos de versión. Una función insertada se expande para crear el código de aplicación; por lo tanto, si más adelante vuelve a escribir la función, no se actualiza a menos que se vuelve a compilar la aplicación en Sí. Normalmente, las funciones DLL se pueden actualizar sin volver a generar las aplicaciones que usan.

## <a name="exporting-individual-members-in-a-class"></a>Exportar a miembros individuales de una clase

A veces es posible que desee exportar a miembros individuales de la clase. Por ejemplo, si va a exportar un `CDialog`-clase derivada, solo es posible que deba exportar el constructor y el `DoModal` llamar. Puede usar `AFX_EXT_CLASS` en los miembros individuales que desea exportar.

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

Dado que ya no va a exportar a todos los miembros de la clase, que pueden surgir un problema adicional debido a la manera en que funcionan las macros MFC. Algunas de las macros de aplicación auxiliar de MFC realmente declaran ni definen a miembros de datos. Por lo tanto, estos miembros de datos deben exportarse desde el archivo DLL.

Por ejemplo, el `DECLARE_DYNAMIC` macro se define como sigue cuando se crea un archivo DLL de extensión MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

La línea que comienza con estático `AFX_DATA` se declara un objeto estático dentro de la clase. Para exportar correctamente esta clase y tener acceso a la información de tiempo de ejecución desde un archivo ejecutable del cliente, debe exportar este objeto estático. Dado que el objeto estático se declara con el modificador `AFX_DATA`, solo necesita definir `AFX_DATA` sea `__declspec(dllexport)` al compilar el archivo DLL y definirlo como `__declspec(dllimport)` al compilar el archivo ejecutable cliente. Dado que `AFX_EXT_CLASS` ya está definida de esta manera, basta con volver a definir `AFX_DATA` sea el mismo que `AFX_EXT_CLASS` en torno a la definición de clase.

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

Dado que MFC utiliza siempre la `AFX_DATA` símbolos en los elementos de datos define dentro de las macros, esto funciona técnica para todos estos escenarios. Por ejemplo, funciona para `DECLARE_MESSAGE_MAP`.

> [!NOTE]
>  Si va a exportar toda la clase en lugar de los miembros seleccionados de la clase, se exportan automáticamente los miembros de datos estáticos.

### <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

- [Exportar desde un archivo DLL mediante archivos .def](../build/exporting-from-a-dll-using-def-files.md)

- [Exportar desde un archivo DLL mediante__declspec (dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportar funciones de C++ para utilizarlas en ejecutables en lenguaje C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funciones de C para utilizarlas en ejecutables en C o C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar qué método de exportación para usar](../build/determining-which-exporting-method-to-use.md)

- [Importar a una aplicación mediante __declspec (dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializar un archivo DLL](../build/run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Nombres representativos](../build/reference/decorated-names.md)

- [Importar y exportar funciones inline](../build/importing-and-exporting-inline-functions.md)

- [Importaciones mutuas](../build/mutual-imports.md)

## <a name="see-also"></a>Vea también

[Exportación desde un archivo DLL](../build/exporting-from-a-dll.md)
