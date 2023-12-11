# 5001_Final_Project_Zihao_Li

Student Name: Zihao Li
Github Username: lizihao 159
Semester: 2023 Fall
Course: CS 5001

# Description

This is a platform jumping game, similar to Mario style. There are 6 levels in total, starting from the first platform. First, you can see the game map from the Overworld panel. After passing the current level, the next level will be unlocked. You can enter the corresponding level by pressing the space bar. Previous and next levels can be accessed via the forward and backward keys. After entering the level, there are gold coins and health indicators in the upper left corner. A gold gold coin is 3 points, and a silver gold coin is 1 point. There are also enemies on some platforms, and the enemies will move around. Once the player collides with the enemy, 20 health points will be deducted, for a total of 100 health points. If the player accidentally falls, his health will be reset to zero and will return to the Overworld. Collision with the hat at the end of the level means passing the level and unlocking the next level. The player's movement can be controlled through the direction keys, and the space is used to jump. If the player jumps on an enemy's head, the enemy will be killed.

# Key Features

I used a game level designer called Tiled to design the levels and exported the level files into .csv format data files. Then design corresponding functions to import the positions of platforms, enemies, and coins in the level:

"""
def import_csv_layout(path):
    terrain_map = []
    with open(path) as map:
        level = reader(map,delimiter = ',')
        for row in level:
            terrain_map.append(list(row))
    return terrain_map
    """

Then use another function to render each pixel at the specified position:

'''
def import_cut_graphics(path):
    surface = pygame.image.load(path).convert_alpha()
    tile_num_x = int(surface.get_size()[0]/tile_size)
    tile_num_y = int(surface.get_size()[1]/tile_size)
    
    cut_tiles = []
    for row in range(tile_num_y):
        for col in range(tile_num_x):
            x = col * tile_size
            y = row * tile_size
            new_surf = pygame.Surface((tile_size,tile_size), flags = pygame.SRCALPHA)# SRCALPHA is for transparency the block we used so that the background can be seen
            new_surf.blit(surface,(0,0),pygame.Rect(x,y,tile_size,tile_size))
            cut_tiles.append(new_surf)
'''

# Guide

Before running the project, the three folders second_part, graphics and levels should be placed at the same level. Then open the code folder in second_part, find the main.py file, and run it using Python idle like(vscode,pycharm)

# Installation Instructions

To run this project locally, please install pygame by typing pip install pygame in the command center

# Code Review

see the comments and docstring in the code files

# Major Challenges

The most challenging part was how to create the animation effect, after searching for information online. I found that I needed to import a folder containing multiple consecutive pictures, obtain their frame numbers, and randomly select pictures to make the picture move.

'''
class AnimatedTile(Tile):
    def __init__(self, size, x, y, path):
        super().__init__(size,x,y)
        self.frames = import_folder(path)
        self.frame_index = 0
        self.image = self.frames[self.frame_index]
        
        
    def animate(self):
        self.frame_index += 0.15
        if self.frame_index >= len(self.frames):
            self.frame_index = 0
        self.image = self.frames[int(self.frame_index)]
        
    def update(self, shift):
        self.rect.x += shift
        self.animate()
'''

# Example Runs

see the following link

# Testing
https://youtu.be/_qvem17kNXg

# Missing Features / What's Next

I didn't add music to the background and beats, so the interactivity was diminished. Additionally, other decorative elements such as grass, rocks, sky, and water are not included in the level design. More importantly, there is no archive function. If I have more time, I will also make a score ranking list to allow players to record scores and clearance time.

# Final Reflection

My semester was an amazing experience with CS5001, a course I had never touched before. The process of learning code was tortuous for me, but also very interesting. In the process, I gradually felt how code can help people in real life. In addition, I also understood the principles and logic behind the software. In addition to the increase in knowledge, I also learned how to solve difficult problems in the code and find bugs by writing test functions. This was an unforgettable experience for me, and I will be able to improve myself in learning other languages in the future through a deeper understanding.




