# Automated Mockups

Welcome to the **Automated Mockups Project!**! This system will help you to adding several photos of yours into your desired Mockups

## Live App

🚧 **On Building**

## Project Status

🚧 **Status**: `On Development`

## Features

- Inputting Images into Spesific Mockups
- The Mockups have to give a very different and Unique Color Boxes to make the system able to detect the mockups target
- You also can edit the mockups parameter on <.JSON> file

## Technologies

- **Python**: Data processing and visualizations
- **Pillow**: Map visualizations
- **CV2**: Map visualizations
- **scikit-image**: Image Detection and Visualization
- **NumPy**: Image Plotting

## Setup

1. Clone the repository:
    ```bash
    git clone https://github.com/Bayhaqieee/Automated_Mockups.git
    ```

2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3. Step 1: Prepare Your Files and Directories

Prepare your directories for your design images, mockup images, and outputs (if they don't yet exist). Also, prepare your design images and place color boxes where you want your designs to be positioned on your mockup images. You can use any available software (e.g. Photoshop, GIMP). The color of the box should be unique and not utilized elsewhere in your images. Then export the mockups to a different directory but with the same name.

Your directory structure should look like this:

```
my_directory
├── designs
│   ├── design1.png
│   ├── design2.jpg
│   └── ...
├── mockups
│   ├── mockup1.png
│   ├── mockup2.jpg
│   └── ...
├── box_mockups
│   ├── mockup1.png
│   ├── mockup2.jpg
│   └── ...
└── output
```

4. Step 2: Calculate Parameters

The second step is to calculate the bounding box parameters for your mockup images. It identifies a specific color in your image (for example, a black box), and calculates the position, size, and rotation of this box.

Run the `calculate_box_pos.py` script by passing the RGB or HEX color, and directory for the mockup images as command-line arguments:

```sh
python calculate_box_pos.py --color R G B --dir image_directory
```

or

```sh
python calculate_box_pos.py --hex_color HEX --dir image_directory
```

Replace `R G B` with the RGB values of the color in your image and `HEX` with the Hexadecimal value of the color. Replace `image_directory` with the directory that holds your mockup images. This will generate a `parameters.json` file with the calculated parameters.

5. Create Mockups

In the third step, use the calculated parameters to position your designs onto the product mockups.

Run the `create_mockups.py` script by passing the paths to the parameters file, design images directory, mockup images directory, and the output directory as command-line arguments:

```sh
python create_mockups.py --param_file parameters.json --design_dir design_directory --mockup_dir mockup_directory --output_dir output_directory
```

Replace `design_directory`, `mockup_directory`, and `output_directory` with the corresponding directory paths.

## Example:

```sh
python calculate_box_pos.py --color 0 0 0 --dir box_mockups
python create_mockups.py --param_file parameters.json --design_dir designs --mockup_dir mockups --output_dir output
```
or

```sh
python calculate_box_pos.py --hex_color #000000 --dir box_mockups
python create_mockups.py --param_file parameters.json --design_dir designs --mockup_dir mockups --output_dir output
```

In the above examples, the scripts will look for black color (0, 0, 0 in RGB or #000000 in HEX format) in images located in the `box_mockups` directory. The positioned images will then be saved in the `output` directory.