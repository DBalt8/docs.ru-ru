---
title: Руководство по ML.NET. Использование .NET в машинном обучении
description: Узнайте, как выполнять конкретные задачи, которые помогут вам в создании специализированных решений на базе искусственного интеллекта и машинного обучения и интеграции их в свои .NET-приложения.
ms.custom: seodec18
ms.date: 03/01/2019
ms.openlocfilehash: c8d1258629f777cd8bced47e4b956c9cf100a682
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427586"
---
# <a name="net-machine-learning-how-to-guides---mlnet"></a><span data-ttu-id="7b4cd-103">Руководство по ML.NET. Использование .NET в машинном обучении</span><span class="sxs-lookup"><span data-stu-id="7b4cd-103">.NET Machine learning how-to guides - ML.NET</span></span>

<span data-ttu-id="7b4cd-104">В практическом руководстве по ML.NET в разделе с инструкциями содержатся ответы на часто задаваемые вопросы.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-104">In the How to section of the ML.NET Guide, you can find quick answers to common questions.</span></span> <span data-ttu-id="7b4cd-105">В некоторых случаях для облегчения поиска статьи могут быть указаны в нескольких разделах.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-105">In some cases, articles may be listed in multiple sections to make them easy to find.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="7b4cd-106">Загрузка данных</span><span class="sxs-lookup"><span data-stu-id="7b4cd-106">Load the data</span></span>

* [<span data-ttu-id="7b4cd-107">Загрузка данных с множеством столбцов из CSV-файла для обработки с помощью машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-107">Load data with many columns from a CSV file for machine learning processing.</span></span>](load-data-from-mult-column-csv-ml-net.md)

* [<span data-ttu-id="7b4cd-108">Загрузка данных из множества файлов для обработки с помощью машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-108">Load data from multiple files for machine learning processing.</span></span>](load-data-from-multiple-files-ml-net.md)

* [<span data-ttu-id="7b4cd-109">Загрузка данных из текстовых файлов для обработки с помощью машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-109">Load data from a text file for machine learning processing.</span></span>](load-data-from-text-file-ml-net.md)

### <a name="prepare-the-data"></a><span data-ttu-id="7b4cd-110">Подготовка данных</span><span class="sxs-lookup"><span data-stu-id="7b4cd-110">Prepare the data</span></span>

* [<span data-ttu-id="7b4cd-111">Предобработка данных для обучения с помощью методов нормализации для использования при обработке данных.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-111">Preprocess training data with normalizers to use in data processing.</span></span>](normalizers-preprocess-data-ml-net.md)

## <a name="train-the-model"></a><span data-ttu-id="7b4cd-112">Обучение модели</span><span class="sxs-lookup"><span data-stu-id="7b4cd-112">Train the model</span></span>

* [<span data-ttu-id="7b4cd-113">Обучение модели машинного обучения, данные для которой находятся не в текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-113">Train a machine learning model with data that's not in a text file.</span></span>](load-non-file-training-data-ml-net.md)

* [<span data-ttu-id="7b4cd-114">Обучение модели машинного обучения с помощью перекрестной проверки.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-114">Train a machine learning model using cross-validation.</span></span>](train-cross-validation-ml-net.md)

* [<span data-ttu-id="7b4cd-115">Обучение регрессионной модели для прогнозирования значения с помощью ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-115">Train a regression model to predict a value using ML.NET.</span></span>](train-regression-model-ml-net.md)

### <a name="evaluate-the-model-quality"></a><span data-ttu-id="7b4cd-116">Оценка качества модели</span><span class="sxs-lookup"><span data-stu-id="7b4cd-116">Evaluate the model quality</span></span>

* [<span data-ttu-id="7b4cd-117">Расчет метрик для оценки качества моделей.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-117">Calculate metrics to evaluate model quality.</span></span>](verify-model-quality-ml-net.md)

### <a name="model-explainability"></a><span data-ttu-id="7b4cd-118">Объясняемость модели</span><span class="sxs-lookup"><span data-stu-id="7b4cd-118">Model explainability</span></span>

* [<span data-ttu-id="7b4cd-119">Определение важности функций моделей с помощью средства Permutation Feature Importance.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-119">Determine the feature importance of models with Permutation Feature Importance.</span></span>](determine-global-feature-importance-in-model.md)

* [<span data-ttu-id="7b4cd-120">Использование обобщенных аддитивных моделей и функций фигур для объясняемости модели.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-120">Use Generalized Additive Models and shape functions for model explainability.</span></span>](use-gams-for-model-explainability.md)

### <a name="feature-engineering"></a><span data-ttu-id="7b4cd-121">Проектирование признаков</span><span class="sxs-lookup"><span data-stu-id="7b4cd-121">Feature engineering</span></span>

* [<span data-ttu-id="7b4cd-122">Применение конструирования признаков для обучения модели по текстовым данным.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-122">Apply feature engineering for model training on categorical data.</span></span>](train-model-categorical-ml-net.md)

* [<span data-ttu-id="7b4cd-123">Применение конструирования признаков для обучения модели по текстовым данным с помощью ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-123">Apply feature engineering for model training on textual data with ML.NET.</span></span>](train-model-textual-ml-net.md)

## <a name="run"></a><span data-ttu-id="7b4cd-124">Выполнить</span><span class="sxs-lookup"><span data-stu-id="7b4cd-124">Run</span></span>

* [<span data-ttu-id="7b4cd-125">Проверка значений промежуточных данных при конвейерной обработке ML.NET.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-125">Inspect intermediate data values during ML.NET pipeline processing.</span></span>](inspect-intermediate-data-ml-net.md)

* [<span data-ttu-id="7b4cd-126">Реализация обученной модели машинного обучения в приложениях.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-126">Operationalize a trained machine learning model in apps.</span></span>](consuming-model-ml-net.md)

* [<span data-ttu-id="7b4cd-127">Использование PredictionFunction для поочередного прогнозирования.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-127">Use the PredictionFunction to make one prediction at a time.</span></span>](single-predict-model-ml-net.md)

## <a name="probabilistic-infernet"></a><span data-ttu-id="7b4cd-128">Вероятностное обучение (Infer.NET)</span><span class="sxs-lookup"><span data-stu-id="7b4cd-128">Probabilistic (Infer.NET)</span></span>

* [<span data-ttu-id="7b4cd-129">Создание приложения со списком матчей с помощью Infer.NET и вероятностного программирования.</span><span class="sxs-lookup"><span data-stu-id="7b4cd-129">Create a game match up list app with Infer.NET and probabilistic programming.</span></span>](matchup-app-infer-net.md)