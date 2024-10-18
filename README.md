<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Comprehensive Digital Image Processing Tool 2024</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 40px;
        }
        h1, h2, h3 {
            color: #2E8B57;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        table, th, td {
            border: 1px solid #000;
        }
        th, td {
            padding: 10px;
            text-align: left;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border: 1px solid #ddd;
        }
    </style>
</head>
<body>

    <h1>Sri Lanka Institute of Information Technology</h1>
    <h2>Comprehensive Digital Image Processing Tool 2024</h2>

    <table>
        <tr>
            <th>Registration Number</th>
            <th>Student Name</th>
        </tr>
        <tr>
            <td>IT17026444</td>
            <td>D.H Gunathilaka</td>
        </tr>
    </table>

    <h2>1. Introduction</h2>
    <p>Image manipulation is an integral part of modern-day applications, offering extensive use cases such as enhancing photo quality, segmenting specific objects, or even generating AI-driven art. This project revolves around creating an interactive tool that performs diverse image manipulations, including grayscale conversion, segmentation, and style transfer using deep learning models. By incorporating popular deep learning architectures like VGG-19, the tool combines both conventional image processing techniques and advanced AI-driven image generation.</p>
    <p>In this report, we delve into the core functionalities of this tool, explaining the underlying algorithms and deep learning models. Additionally, code snippets provide insights into the practical implementation of these features.</p>

    <h2>2. Background Information on Algorithms Used</h2>
    <h3>2.1. Image Manipulation Algorithms</h3>
    <ul>
        <li><strong>Color Adjustment:</strong> Image color properties such as saturation, hue, and lightness can be adjusted dynamically by transforming the image into different color spaces (e.g., HSV) and applying appropriate scaling factors. Saturation adjustment enhances the vividness of the image colors, while hue shifts the overall color tone. Lightness controls the brightness and contrast of the image.</li>
        <li><strong>Grayscale Conversion:</strong> A classic image processing technique, grayscale conversion transforms a color image into shades of gray, removing the color information while preserving the structural details of the image. This transformation simplifies image analysis for tasks like edge detection.</li>
        <li><strong>Black and White Conversion (Binarization):</strong> In this technique, pixel intensities are converted into two distinct values (black or white) based on a threshold. This method is useful for simplifying the image when analyzing features such as text or clear boundaries in the image.</li>
        <li><strong>Image Segmentation:</strong> The goal of image segmentation is to partition an image into meaningful segments or objects. By utilizing color-based segmentation through the HSV color space, the application isolates specific regions of the image that fall within a given range of colors, allowing for further manipulation.</li>
    </ul>

    <h3>2.2. Deep Learning-Based Neural Style Transfer</h3>
    <p>Neural Style Transfer (NST) is an AI-driven technique that combines the content of one image with the style of another. This technique utilizes deep convolutional neural networks, particularly models like VGG-19, to extract and blend the content and style features of two images.</p>
    <ul>
        <li><strong>Content Image:</strong> The image whose underlying structure (shapes, objects) is retained.</li>
        <li><strong>Style Image:</strong> The image whose artistic features (colors, textures, patterns) are transferred.</li>
    </ul>
    <p>The algorithm relies on the output of specific layers from the pre-trained VGG-19 model, which serves as a feature extractor. The Gram matrix is computed to capture the correlations between different filters in the style image, while the content layers preserve the spatial arrangement of objects in the content image.</p>

    <h3>2.3. Filters</h3>
    <p>The application of image filters is handled through PIL’s ImageFilter module, which allows for real-time adjustments such as:</p>
    <ul>
        <li><strong>Sharpening:</strong> Enhances edges and detail.</li>
        <li><strong>Blurring:</strong> Softens the image, useful for creating a dreamy or out-of-focus effect.</li>
        <li><strong>Edge Detection:</strong> Highlights the edges of objects, providing a stark contrast.</li>
        <li><strong>Embossing:</strong> Creates a raised effect that simulates depth on the image surface.</li>
    </ul>

    <h2>3. Model Architectures</h2>
    <h3>3.1. VGG-19 Architecture</h3>
    <p>The VGG-19 model used in neural style transfer is a deep convolutional neural network originally designed for image classification tasks. It consists of 19 layers, including 16 convolutional layers and 3 fully connected layers. For the purpose of style transfer, the fully connected layers are discarded, and only the convolutional layers are used to extract style and content features.</p>
    <ul>
        <li><strong>Content Layers:</strong> Primarily deeper layers (e.g., block5_conv2), which retain the structural information of the image.</li>
        <li><strong>Style Layers:</strong> Early layers (e.g., block1_conv1, block2_conv1) are used to capture lower-level style features like textures and colors.</li>
    </ul>

    <h3>3.2. Style Transfer Process</h3>
    <ul>
        <li><strong>Preprocessing:</strong> Both content and style images are resized to a uniform dimension and preprocessed to match the input requirements of the VGG-19 model.</li>
        <li><strong>Feature Extraction:</strong> The style and content features are extracted using the selected layers of VGG-19. The Gram matrix is calculated for the style layers to capture correlations between feature maps.</li>
        <li><strong>Optimization:</strong> The input image is initialized as a copy of the content image and optimized iteratively to minimize the content loss and style loss through gradient descent.</li>
        <li><strong>Postprocessing:</strong> The resulting stylized image is post-processed to clip values within a valid range and displayed on the canvas.</li>
    </ul>

    <h2>4. Results</h2>
    <h3>4.1. Image Manipulation</h3>
    <p>The developed tool allows users to perform basic and advanced image manipulations such as cropping, rotating, flipping, and color adjustments. These operations were tested with various images, and the tool successfully handled the transformations with real-time visual feedback on the canvas.</p>
    <ul>
        <li><strong>Grayscale Conversion:</strong> Efficiently converted images into grayscale, maintaining structural details while removing color information.</li>
        <li><strong>Black and White Conversion:</strong> The binarization process worked well for text-heavy images, highlighting the boundaries with clear distinction.</li>
        <li><strong>Segmentation:</strong> The color-based segmentation proved effective in isolating objects of interest, though the results can vary depending on the initial color distribution of the image.</li>
    </ul>

    <h3>4.2. Neural Style Transfer</h3>
    <p>The neural style transfer functionality produced impressive results, blending the content of one image with the artistic features of the style image. For instance, using Van Gogh's <em>Starry Night</em> as a style image and various user-selected content images, the application successfully transferred the swirling brushstrokes and vibrant colors of the style image while preserving the fundamental structure of the content image.</p>
    <ul>
        <li><strong>Content Preservation:</strong> The shapes and major objects from the content image were well-preserved.</li>
        <li><strong>Artistic Style:</strong> The texture, color palette, and artistic feel from the style image were accurately transferred, creating a visually pleasing result.</li>
    </ul>

    <h3>4.3. Filters and Adjustments</h3>
    <p>The various filters allowed users to apply artistic effects to images in real-time. The strength of each filter was adjustable, enabling fine control over the intensity of the effect. The application demonstrated good performance even with large images, delivering smooth transitions between filter effects.</p>

    <h2>5. Conclusion</h2>
    <p>The developed image manipulation and neural style transfer tool presents a powerful platform for performing complex image transformations. With its intuitive GUI, users can easily interact with the tool to enhance, modify, and stylize images. The combination of traditional image processing techniques and modern deep learning algorithms like neural style transfer offers a wide range of creative possibilities for artists, photographers, and AI enthusiasts alike.</p>
    <p>The results highlight the effectiveness of both manual image adjustments and AI-driven transformations. Moving forward, potential improvements could include real-time style transfer (with reduced latency) and adding additional style transfer models or other advanced techniques like super-resolution.</p>
    <p>This tool is an excellent starting point for exploring the capabilities of deep learning in image manipulation and art creation, demonstrating the intersection of art and technology.</p>

</body>
</html>
