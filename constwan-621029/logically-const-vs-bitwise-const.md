### logically const vs bitwise const

"Physical" constness comes from declaring an object const, and could, in principle, be enforced by placing the object in read-only memory, so it cannot change. Attempting to change it will cause undefined behaviour; it might change, or it might not, or it might trigger a protection fault, or it might melt the memory chip.