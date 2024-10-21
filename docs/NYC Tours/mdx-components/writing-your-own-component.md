---
title: Writing your own Component
deprecated: false
hidden: false
metadata:
  robots: index
---
export const Icon = ({ style = 'fa-regular', name }) => <i className={`${style} ${name}`} />;

export const Columns = ({ children }) => <div style={{ display: 'flex' }}>{children}</div>;

export const Column = ({ children }) => <div style={{ flex: 1, padding: '0 10px' }}>{children}</div>;

export const Highlight = ({ children, color = 'lightyellow' }) => (    
  <span style={{ backgroundColor: color }}>{children}</span>
);

export const Color = ({ children, color }) => (    
  <span style={{ color }}>{children}</span>
);

export const Gradient = ({ children, start, stop, color = 'white' }) => (    
  <div style={{ background: `linear-gradient(${start}, ${stop})`, color: color, padding: '10px' }}>
    {children}
  </div>
);

export const Sparkle = ({ children }) => {  
  const sparkleColors = ['#FFD700', '#FF69B4', '#00FFFF', '#FF4500', '#ADFF2F'];  
  const randomColor = () => sparkleColors[Math.floor(Math.random() * sparkleColors.length)];

  return (  
    <div style={{ position: 'relative', display: 'inline-block' }}>  
      {children}  
      {[...Array(5)].map((_, index) => (  
        <span  
          key={index}  
          style={{  
            position: 'absolute',  
            top: `${Math.random() * 60 - 30}%`,  // Subtract 20% from the top value  
            left: `${index * 20 + 10}%`,        // Evenly spaced across the width  
            color: randomColor(),  
            animation: `sparkle 1.5s infinite ${Math.random()}s`,  
            pointerEvents: 'none',  
            transform: 'translate(-50%, -50%)',  
            zIndex: 100,  
          }}  
        >  
          <Icon style="fa-regular" name="fa-star" />  
        </span>  
      ))}  
      <style jsx>{`        @keyframes sparkle {
          0%, 100% { opacity: 0; transform: scale(0.5) rotate(0deg); }
          50% { opacity: 1; transform: scale(1) rotate(45deg); }
        }
     `}</style>  
    </div>  
  );  
};

# Example Usage of Components

Here's how you can use these components in your MDX content:

## Icons

<Icon name="fa-coffee" /> Good morning! Here's a cup of coffee with your MDX.

## Columns

<Columns>
  <Column>
    This is the first column. It's on the left.
  </Column>

  <Column>
    This is the second column. You can add as many columns as you want.
  </Column>
</Columns>

## Highlighted Text

This text is <Highlight>highlighted in yellow</Highlight>, while this text is <Highlight color="lightblue">highlighted in light blue.</Highlight>

## Colored Text

<Color color="red">This text is red,</Color> and <Color color="green">this text is green.</Color>

## Gradient Background

<Gradient start="blue" stop="green" color="#fff">
  This text has a gradient background from blue to green with white text.
</Gradient>

## Sparkle Effect

<Sparkle>
  This text has little sparkles that pop up over it.
</Sparkle>